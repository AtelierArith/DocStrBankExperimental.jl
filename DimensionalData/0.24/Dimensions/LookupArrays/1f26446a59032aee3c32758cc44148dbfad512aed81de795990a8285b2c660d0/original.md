```
Metadata <: AbstractMetadata

Metadata{X}(val::Union{Dict,NamedTuple})
Metadata{X}(pairs::Pair...) => Metadata{Dict}
Metadata{X}(; kw...) => Metadata{NamedTuple}
```

General [`Metadata`](@ref) object. The `X` type parameter categorises the metadata for method dispatch, if required. 
