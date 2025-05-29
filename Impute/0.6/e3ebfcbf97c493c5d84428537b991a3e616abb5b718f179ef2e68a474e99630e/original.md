```
impute!(data::T, imp; kwargs...) -> T where T <: AbstractVector{<:NamedTuple}
```

Special case rowtables which are arrays, but we want to fallback to the tables method.
