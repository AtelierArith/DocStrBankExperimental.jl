```
struct ScalarCondition{U,FT<:AbstractFeature,M<:ScalarMetaCondition{FT}} <: AbstractCondition{FT}
    metacond::M
    a::U
end
```

A scalar condition comparing a computed feature value (see `ScalarMetaCondition`) and a threshold value `a`. It can be evaluated on a world of an instance of a logical dataset.

For example: $min[V1] ≥ 10$, which translates to "Within this world, the minimum of variable 1 is greater or equal than 10." In this case, the feature a [`VariableMin`](@ref) object.

See also [`AbstractCondition`](@ref), [`ScalarMetaCondition`](@ref).
