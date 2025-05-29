```
LineIterator(path::String; filestart = 1, structtype = nothing)
```

Create an iterator of a JSONLines file at `path`.

  * Keyword Arguments:

      * `filestart=1`: Row at which to start the iterator
      * `structtype=nothing`: StructType passed to `JSON3.read` for each row
