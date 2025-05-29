```
Base.@kwdef struct Argo_pq
    Dataset  ::Parquet2.Dataset
    schema   ::Tables.Schema
    files    ::Vector
    folder   ::String
end
```
