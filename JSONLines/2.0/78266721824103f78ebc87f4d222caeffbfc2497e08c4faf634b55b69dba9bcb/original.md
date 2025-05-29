```
writelines(path::String, rows; nworkers = 1, mode = "w")
```

Write `rows` to JSONLines file `path`

  * `path`: Path to output file
  * `rows`: `Tables.jl` compatible data
  * Keyword Arguments:

      * `nworkers=1`: Number of threads to use for parsing to JSONLines
      * `mode="w"`: Mode the file is opened in. [See I/O and Network](https://docs.julialang.org/en/v1/base/io-network/)
