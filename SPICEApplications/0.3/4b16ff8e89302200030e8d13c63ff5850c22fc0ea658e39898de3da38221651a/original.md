```julia
dskexp(
;
    dsk,
    text,
    format,
    precision,
    stdout,
    stderr,
    stdin,
    append,
    wait
)

```

DSKEXP is a command-line program that exports data from DSK files to text files.

# Extended Help

!!! warning
    All descriptions below were manually parsed from the commandline program's help/usage output.


| Argument    | Equivalent                                  | Description                      |
|:----------- |:------------------------------------------- |:-------------------------------- |
| `dsk`       | `-dsk <dsk>`                                | DSK kernel                       |
| `text`      | `-text <output name>`                       | output name                      |
| `format`    | `-format <MKDSK format code/name>`          | MKSDK format code/name           |
| `precision` | `-prec <# of vertex mantissa digits (1:17)` | number of vertex mantissa digits |
