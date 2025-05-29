```
TransformerError(msg::String)
```

A catch-all for issues involving data transformers, with details given in `msg`.

# Example occurrence

```julia-repl
julia> emptydata = DataSet(DataCollection(), "empty", SmallDict{String, Any}("uuid" => Base.UUID(rand(UInt128))))
DataSet empty

julia> read(emptydata)
ERROR: TransformerError: Data set "empty" could not be loaded in any form.
Stacktrace: [...]
```
