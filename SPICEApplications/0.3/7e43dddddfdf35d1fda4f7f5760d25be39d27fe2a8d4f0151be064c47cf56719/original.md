```julia
commnt(; ...)
commnt(kernelfile; ...)
commnt(
    kernelfile,
    commentfile;
    add,
    extract,
    read,
    delete,
    help,
    stdout,
    stderr,
    stdin,
    append,
    wait
)

```

COMMNT is a command-line program that reads, adds, extracts, or deletes comments from SPICE binary kernel files.

# Extended Help

!!! warning
    All descriptions below were manually parsed from the commandline program's help/usage output.


| Argument  | Equivalent | Description                                |
|:--------- |:---------- |:------------------------------------------ |
| `add`     | `-a`       | add comments to binary kernel              |
| `extract` | `-e`       | extract comments from a binary kernel      |
| `read`    | `-r`       | read the comments in a binary kernel       |
| `delete`  | `-d`       | delete the comments from the binary kernel |
| `help`    | `-h`       | display the help message                   |
