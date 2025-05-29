```julia
ckbrief(
    file;
    dump,
    boundaries,
    relframes,
    idframes,
    tabular,
    single,
    bycoverage,
    utc,
    utcdoy,
    sclk,
    dpsclk,
    id,
    summarize,
    help,
    version,
    stdout,
    stderr,
    stdin,
    append,
    wait
)

```

CKBRIEF is a command-line utility program that displays a contents and time coverage summary for one or more binary CK files.

# Extended Help

!!! warning
    All descriptions below were manually parsed from the commandline program's help/usage output.


| Argument     | Equivalent | Description                                   |
|:------------ |:---------- |:--------------------------------------------- |
| `dump`       | `-dump`    | display interpolation intervals boundaries    |
| `boundaries` | `-nm`      | display segment boundaries                    |
| `relframes`  | `-rel`     | display relative-to frames                    |
| `idframes`   | `-n`       | display frames associated with structure IDs  |
| `tabular`    | `-t`       | display summary in a tabular format           |
| `single`     | `-a`       | treat all files as a single file              |
| `bycoverage` | `-g`       | display summary grouped by coverage           |
| `utc`        | `-utc`     | display times in UTC calendar date format     |
| `utcdoy`     | `-utcdoy`  | display times in UTC day-of-year format       |
| `sclk`       | `-sclk`    | display times as SCLK strings                 |
| `dpsclk`     | `-dpsclk`  | display times as SCLK ticks                   |
| `id`         | `[ID]`     | display summmary for structure with [ID]      |
| `summarize`  | `-f`       | summarize kernels listed in the `[list]` file |
| `help`       | `-h`       | display help                                  |
| `version`    | `-v`       | display version                               |
