# Findings Tracker

## Assessment context

| Field | Value |
| --- | --- |
| Environment | Authorized TryHackMe Dreaming laboratory |
| Assessment stage | Web reconnaissance and validation of exposed paths |
| Recorded target | `10.49.166.183` — expired; retained only as historical evidence |
| Completion state | No exploitation, privilege escalation, or flag recovery recorded |

## Tracked observations

| ID | Observation | Evidence | Status | Assessment |
| --- | --- | --- | --- | --- |
| F-01 | Pluck CMS 4.7.13 was identified. | `admin.php` title and visible copyright; `/docs/README`. | Verified | Informational software identification. |
| F-02 | `/admin.php`, `/login.php`, and `/install.php` were reachable. | Gobuster output showed HTTP 200 for each endpoint. | Verified | Review on a restarted lab machine; reachability alone is not a vulnerability. |
| F-03 | `/data/`, `/docs/`, `/files/`, and `/images/` were discovered. | Gobuster output showed HTTP 301 directory redirects. | Verified | Informational attack-surface inventory. |
| F-04 | `/docs/` allowed directory listing of standard Pluck files. | Captured listing included `CHANGES`, `COPYING`, `README`, `UPDATING`, and `update.php`. | Verified | Low-risk information exposure in the observed session; contents appeared to be standard product documentation. |
| F-05 | `/robots.txt` contained `Disallow: /data/`. | Direct `curl` output. | Verified | Informational; `robots.txt` is not access control. |
| F-06 | `data/settings/options.php` and `data/settings/pass.php` returned HTTP 200 with zero visible content. | Captured `curl -i` responses. | Verified observation | No credential or configuration exposure was demonstrated. Do not classify as a leak without content. |
| F-07 | Additional paths named `settings`, `modules`, `themes`, `trash`, and `inc` were enumerated under the data area. | Follow-up directory scan output. | Verified observation | Needs controlled review only in a fresh authorized lab session. |

## Evidence references


| Evidence | Relevant screenshots |
| --- | --- |
| Initial and ongoing Gobuster enumeration | `09-directory-enumeration-start.png`, `07-directory-enumeration-progress.png`, `04-directory-enumeration.png` |
| Completed root enumeration | `01-directory-enumeration-complete.png`, `02-discovered-directories.png` |
| Data/settings response checks | `05-http-response-check.png` |
| Additional enumeration output | `03-enumeration-detail.png`, `06-directory-enumeration-run.png`, `08-enumeration-findings.png` |


## Constraints and next steps

The source lab instance expired before the work could continue. Any continuation must use a newly assigned TryHackMe target, revalidate every result, and document only evidence obtained within that authorized session.
