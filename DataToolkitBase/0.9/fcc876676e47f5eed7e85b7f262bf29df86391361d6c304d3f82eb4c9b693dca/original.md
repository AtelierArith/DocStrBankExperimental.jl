```
UnsatisfyableTransformer{T}(dataset::DataSet, types::Vector{QualifiedType})
```

A transformer (of type `T`) that could provide any of `types` was asked for, but there is no transformer that satisfies this restriction.

# Example occurrence

```julia-repl
julia> emptydata = DataSet(DataCollection(), "empty", SmallDict{String, Any}("uuid" => Base.UUID(rand(UInt128))))
DataSet empty

julia> read(emptydata, String)
ERROR: UnsatisfyableTransformer: There are no loaders for "empty" that can provide a String. The defined loaders are as follows:
Stacktrace: [...]
```
