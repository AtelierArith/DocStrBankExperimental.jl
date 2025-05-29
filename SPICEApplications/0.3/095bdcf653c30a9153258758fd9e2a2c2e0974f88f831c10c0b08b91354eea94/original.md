```julia
chronos(
    file;
    from,
    fromtype,
    to,
    totype,
    format,
    time,
    sc,
    center,
    landingtime,
    sol1index,
    nolabel,
    trace,
    help,
    usage,
    template,
    stdout,
    stderr,
    stdin,
    append,
    wait
)

```

CHRONOS is a command-line program that converts between several time systems and time formats.

# Extended Help

!!! warning
    All descriptions below were manually parsed from the commandline program's help/usage output.


| Argument      | Equivalent                               | Description                 |
|:------------- |:---------------------------------------- |:--------------------------- |
| `from`        | `-FROM <"from" time system>`             | "from" time system          |
| `fromtype`    | `-FROMTYPE <"from" time system type>`    | "from" time system type     |
| `to`          | `-TO <"to" time system>`                 | "to" time system            |
| `totype`      | `-TOTYPE <"to" time system type>`        | "to" time system  type      |
| `format`      | `-FORMAT <output time format picture>`   | output time format picture  |
| `time`        | `-TIME <input time>`                     | intput time                 |
| `sc`          | `-SC <sc ID>`                            | sc ID                       |
| `center`      | `-CENTER <cental body ID>`               | cental body ID              |
| `landingtime` | `-LANDINGTIME <UTC time of the landing>` | UTC time of the landing     |
| `sol1index`   | `-SOL1INDEX <index of the first SOL>`    | index of the first SOL      |
| `nolabel`     | `-NOLABEL`                               |                             |
| `trace`       | `-TRACE`                                 |                             |
| `help`        | `-HELP`                                  | display help                |
| `usage`       | `-USAGE`                                 | display usage               |
| `template`    | `-TEMPLATE`                              | display setup file template |
