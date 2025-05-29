```julia
mkdsk(
;
    setup,
    input,
    output,
    help,
    template,
    usage,
    version,
    stdout,
    stderr,
    stdin,
    append,
    wait
)

```

MKDSK is a utility program that creates a SPICE Digital Shape Kernel (DSK) file from a text file containing shape data for an extended object.

# Extended Help

!!! warning
    All descriptions below were manually parsed from the commandline program's help/usage output.


| Argument   | Equivalent                            | Description                |
|:---------- |:------------------------------------- |:-------------------------- |
| `setup`    | `-setup <setup file name>`            | setup file name            |
| `input`    | `-input <input shape data file name>` | input shape data file name |
| `output`   | `-output <output DSK file name>`      | output DSK file name       |
| `help`     | `-h│-help`                            | display help               |
| `template` | `-t│-template`                        | display template           |
| `usage`    | `-u│-usage`                           | display usage              |
| `version`  | `-v│-version`                         | display version            |
