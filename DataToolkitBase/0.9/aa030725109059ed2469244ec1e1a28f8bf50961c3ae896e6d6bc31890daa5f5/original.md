```
fromspec(ADT::Type{<:AbstractDataTransformer}, dataset::DataSet, spec::Dict{String, Any})
```

Create an `ADT` of `dataset` according to `spec`.

`ADT` can either contain the driver name as a type parameter, or it will be read from the `"driver"` key in `spec`.
