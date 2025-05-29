```julia
mkspk(
;
    setup,
    input,
    output,
    add,
    usage,
    help,
    template,
    stdout,
    stderr,
    stdin,
    append,
    wait
)

```

MKSPK is a program that creates an SPK file from a text file containing trajectory information.

# Extended Help

!!! warning
    All descriptions below were manually parsed from the commandline program's help/usage output.


| Argument   | Equivalent                            | Description                     |
|:---------- |:------------------------------------- |:------------------------------- |
| `setup`    | `-setup <setup file name>`            | setup file name                 |
| `input`    | `-input <input shape data file name>` | input shape data file name      |
| `output`   | `-output <output DSK file name>`      | output DSK file name            |
| `add`      | `-append`                             | append; output file must be new |
| `help`     | `-h│-help`                            | display help                    |
| `template` | `-t│-template`                        | display template                |
| `usage`    | `-u│-usage`                           | display usage                   |
