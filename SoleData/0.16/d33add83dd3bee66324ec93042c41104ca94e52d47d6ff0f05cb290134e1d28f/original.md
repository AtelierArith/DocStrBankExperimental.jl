```
struct FunctionalCondition{FT<:AbstractFeature} <: AbstractCondition{FT}
    feature::FT
    f::FT
end
```

A condition which yields a truth value equal to the value of a function.

See also [`AbstractFeature`](@ref).
