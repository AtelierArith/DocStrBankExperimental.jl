```julia
brief(
    file;
    tabular,
    single,
    centers,
    utc,
    utcdoy,
    etsec,
    sec,
    min,
    hour,
    day,
    bytime,
    bycoverage,
    byid,
    byname,
    body,
    center,
    at,
    from,
    to,
    listfile,
    help,
    version,
    stdout,
    stderr,
    stdin,
    append,
    wait
)

```

BRIEF is a command-line utility program that displays a contents and time coverage summary for one or more binary SPK or binary PCK files.

# Extended Help

!!! warning
    All descriptions below were manually parsed from the commandline program's help/usage output.


| Argument     | Equivalent    | Description                                                  |
|:------------ |:------------- |:------------------------------------------------------------ |
| `tabular`    | `-t`          | Display summary in a tabular format                          |
| `single`     | `-a`          | Treat all files as a single file                             |
| `centers`    | `-c`          | Displays centers of motion/relative-to frames                |
| `utc`        | `-utc`        | Display times in UTC calendar date format (needs LSK)        |
| `utcdoy`     | `-utcdoy`     | Display times in UTC day-of-year format (needs LSK)          |
| `etsec`      | `-etsec`      | Display times as ET seconds past J2000                       |
| `sec`        | `-sec`        | Display times "rounded inward" to second                     |
| `min`        | `-min`        | Display times "rounded inward" to minute                     |
| `hour`       | `-hour`       | Display times "rounded inward" to hour                       |
| `day`        | `-day`        | Display times "rounded inward" to day                        |
| `bytime`     | `-s`          | Display summary sorted by start time for each body/frame     |
| `bycoverage` | `-g`          | Display summary grouped by coverage                          |
| `byid`       | `-n`          | Display bodies/frames using numeric id-codes                 |
| `byname`     | `-o`          | Display summary ordered by body/frame name                   |
| `body`       | `-sb[bod]`    | Display summary for body [bod]                               |
| `center`     | `-sc[cen]`    | Display summary for center of motion/relative-to frame [cen] |
| `at`         | `-at [time]`  | Display summary if coverage contains epoch [time]            |
| `from`       | `-from [beg]` | Display summary if coverage contains interval [beg]:[end]    |
| `to`         | `-to [end]`   | Display summary if coverage contains interval [beg]:[end]    |
| `listfile`   | `-f [list]`   | Summarize kernels listed in the [list] file                  |
| `help`       | `-h`          | Display help                                                 |
| `version`    | `-v`          | Display version                                              |
