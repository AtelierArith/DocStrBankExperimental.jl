```
struct ValueCondition{FT<:AbstractFeature} <: AbstractCondition{FT}
    feature::FT
end
```

A condition which yields a truth value equal to the value of a feature.

See also [`AbstractFeature`](@ref).
