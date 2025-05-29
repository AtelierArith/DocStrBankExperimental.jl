```
LineIndex(path::String; filestart::Int = 0, skip::Int = 0, nrows::Int = typemax(Int), structtype = nothing, schemafrom::UnitRange{Int} = 1:10, nworkers::Int = 1)
```

Create an index of a JSONLines file at `path`

  * Keyword Arguments:

      * `filestart=0`: Number of bytes to skip before reading the file
      * `skip=0`: Number of rows to skip before parsing
      * `nrows=typemax(Int)`: Maximum number of rows to index
      * `structtype=nothing`: `StructType` passed to `JSON3.read` for each row
      * `schemafrom=1:10`: Rows to parse initially to determine columnnames and columntypes
      * `nworkers=1`: Number of threads to use for operations on the `LineIndex`
