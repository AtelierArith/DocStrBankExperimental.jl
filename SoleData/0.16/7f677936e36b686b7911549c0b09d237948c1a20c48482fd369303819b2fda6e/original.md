```
struct ScalarMetaCondition{FT<:AbstractFeature,O<:TestOperator} <: AbstractScalarCondition{FT}
    feature::FT
    test_operator::O
end
```

A metacondition representing a scalar comparison method. Here, the `feature` is a scalar function that can be computed on a world of an instance of a logical dataset. A test operator is a binary mathematical relation, comparing the computed feature value and an external threshold value (see `ScalarCondition`). A metacondition can also be used for representing the infinite set of conditions that arise with a free threshold (see `UnboundedScalarAlphabet`): ${min[V1] ≥ a, a ∈ ℝ}$.

See also [`AbstractScalarCondition`](@ref), [`ScalarCondition`](@ref).
