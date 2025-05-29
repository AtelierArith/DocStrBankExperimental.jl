```
InformationMeasureEstimator{I <: InformationMeasure}
```

The supertype of all information measure estimators. Its direct subtypes are [`DiscreteInfoEstimator`](@ref) and [`DifferentialInfoEstimator`](@ref).

Since all estimators must reference a measure definition in some way, we made the following interface decisions:

1. all estimators have as first type parameter `I <: InformationMeasure`
2. all estimators reference the information measure in a `definition` field
3. all estimators are defined using `Base.@kwdef` so that they may be initialized with the syntax `Estimator(; definition = Shannon())` (or any other).

Any concrete subtypes must follow the above, e.g.:

```julia
Base.@kwdef struct MyEstimator{I <: InformationMeasure, X} <: DiscreteInfoEstimator{I}
    definition::I
    x::X
end
```

!!! info "Why separate the *definition* of a measure from *estimators* of a measure?"
    In real applications, we generally don't have access to the underlying probability mass functions or densities required to compute the various entropy or extropy definitons. Therefore, these information measures must be *estimated* from finite data. Estimating a particular measure (e.g. [`Shannon`](@ref) entropy) can be done in many ways, each with its own own pros and cons. We aim to provide a complete library of literature estimators of the various information measures (PRs are welcome!).

