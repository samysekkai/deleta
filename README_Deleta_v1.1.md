# Deleta — Disk Analysis & Safe Cleanup

**Understand your storage. Find unnecessary files. Stay in control.**

Deleta is a Windows disk-analysis assistant designed to help you understand where your storage space is going. Explore large files and folders, inspect possible duplicates, and estimate potential savings before deciding what to keep or remove.

> **Safety first:** Deleta does not automatically delete your files. Review results before taking action. Treat system files (including `.sys` files), application data, and unfamiliar folders as sensitive; do not remove them without verifying their purpose.

## Software version and editions

**Current development version: 1.1** — focused on scanner improvements, more reliable duplicate verification, and better treemap readability.

The **software version** (1.0, 1.1, 1.2…) is different from the **edition** (Basic, Advanced, Plus). The three editions remain available in the project; each edition has a different feature set.

| Feature | Basic | Advanced | Plus |
|---|:---:|:---:|:---:|
| Disk usage overview | ✅ | ✅ | ✅ |
| Folder analysis, largest files and folders | ✅ | ✅ | ✅ |
| Filters and sorting | ✅ | ✅ | ✅ |
| Open items or copy file paths | ✅ | ✅ | ✅ |
| Interactive treemap | — | ✅ | ✅ |
| Duplicate file detection | — | ✅ | ✅ |
| Space-saving simulation (no deletion) | — | — | ✅ |
| Insights | — | — | ✅ |
| CSV export | — | — | ✅ |
| Scan history | — | — | ✅ |

### Basic — Essential disk analysis

<img width="1254" height="916" alt="Screenshot 2026-01-27 224540" src="https://github.com/user-attachments/assets/f00c0de0-38a2-4645-b524-9ccbdaece9ec" />

- Choose a folder to scan and see how much space it contains.
- Find the largest files and folders.
- Filter and sort results by size or age.
- Copy file paths or open their location in Windows Explorer.
- Choose what to remove manually; Deleta does not perform automatic deletion.

### Advanced — Visual exploration and duplicates

<img width="1258" height="911" alt="Screenshot 2026-01-27 224950" src="https://github.com/user-attachments/assets/ce2e326d-c48b-42cb-9f0f-1845095605c4" />

Includes all Basic features, plus:

- **Treemap:** visualize which folders occupy the most space; select blocks to inspect folders.
- **Duplicate detection:** identify identical file candidates and inspect groups before making any decision.

### Plus — Analysis, insights and reporting

<img width="1662" height="916" alt="image" src="https://github.com/user-attachments/assets/14ebd3ef-6fd7-42b8-9e5b-aa3ec4a3235a" />

Includes all Basic and Advanced features, plus:

- **Space-saving simulation:** estimate potential savings without deleting files.
- **Insights:** highlight the largest folders and other key scan results.
- **CSV export:** save analysis results for review.
- **History:** consult summaries of previous scans.

## What's new in Deleta 1.1

Deleta 1.1 improves the existing engine rather than replacing the three editions.

| Area | Version 1.0 | Version 1.1 |
|---|---|---|
| Folder traversal | Recursive directory traversal | Iterative traversal, better suited to deep directory structures |
| Duplicate detection | Partial file hashes used for grouping | Fast initial sampling followed by full SHA-256 verification for candidate groups |
| Duplicate initial sampling | Up to approximately 2 MB per large file | Approximately 128 KB per large file before full verification |
| Old-file selection | Previous oldest-file ranking logic | Updated selection logic; verify its results during testing |
| Progress display | More frequent progress events | Reduced progress update frequency |
| Treemap labels | Labels could overlap in thin blocks | Labels adapt to the available block width and height |

**Performance note:** improvements are intended to reduce unnecessary work and keep the interface responsive. Actual speed gains have **not yet been benchmarked** across different drives and workloads. Full hashing of duplicate candidates can add work, but it improves confidence in the results.

## How to use

1. Open Deleta and choose a folder to scan.
2. Start the analysis and review the largest files, folders and available visualizations.
3. In Advanced or Plus, inspect the treemap and duplicate groups.
4. In Plus, use simulation and reporting to evaluate potential savings.
5. Review any file manually before deleting it with Windows tools.

Large scans may take longer, especially on HDDs, network drives or folders containing many small files. Some protected folders may not be accessible.

## Version history

| Software release | Summary |
|---|---|
| **1.0** | Initial disk analysis, edition-specific tools, treemap, duplicate detection and simulation |
| **1.1** | Scanner improvements, strengthened duplicate verification, progress refinements and improved treemap labels |
| **1.2 (planned)** | Evaluate scan caching, further performance measurements and additional usability improvements |

## Technical notes

- Desktop interface: **Python + PySide6**.
- Charts and treemap: **Matplotlib**.
- Disk inspection: Python file-system APIs, with worker threads to avoid blocking the interface.
- Duplicate verification: SHA-256 hashing of candidates.
- The codebase distinguishes editions through the `APP_EDITION` environment setting (`basic`, `advanced`, `plus`). The development default is `plus`.

This README describes the **1.1 codebase**. Check the release label on the download page to confirm which version is actually distributed; updating this document does not update previously uploaded installers.

## Download Deleta

- [Deleta on itch.io](https://limeiasoft.itch.io/deleta)
- [Deleta on Payhip](https://payhip.com/b/l18z9)

## Why choose Deleta?

- No automatic deletion: you decide what happens to your files.
- Clear visualization of storage usage.
- Tools for finding large files and reviewing duplicates.
- Separate **Basic**, **Advanced**, and **Plus** editions to match different needs.

---

**Deleta — You stay in control.**
