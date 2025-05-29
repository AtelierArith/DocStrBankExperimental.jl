```julia
dskbrief(
    file;
    single,
    gaps,
    extended,
    timebounds,
    bysegment,
    full,
    sigdigs,
    version,
    help,
    usage,
    stdout,
    stderr,
    stdin,
    append,
    wait
)

```

DSKBRIEF is a command-line utility program that displays a summary of the spatial coverage and additional attributes of one or more binary Digital Shape Kernel (DSK) files.

# Extended Help

!!! warning
    All descriptions below were manually parsed from the commandline program's help/usage output.


| Argument     | Equivalent | Description                                                                          |
|:------------ |:---------- |:------------------------------------------------------------------------------------ |
| `single`     | `-a`       | treat all DSK files as a single file                                                 |
| `gaps`       | `-gaps`    | display coverage gaps (aplies only when `-a` is used)                                |
| `extended`   | `-ext`     | display extended summaries: these include data type, data class, and time bounds     |
| `timebounds` | `-tg`      | require segment time bounds to match when grouping segments                          |
| `full`       | `-full`    | display a detailed summary for each segment, including data-type-specific parameters |
| `sigdigs`    | `-d <n>`   | display `n` significant digits of floating point values                              |
| `version`    | `-v`       | display the version of the program                                                   |
| `help`       | `-h`       | display help text                                                                    |
| `usage`      | `-u`       | display usage text                                                                   |
