```
analyse_coordstate(
    d,
    coordState::CoordState,
    anaSpec::AnalysisSpecification,
    stdBasis::StandardBasis=missing,
    kernelPolytope::Union{HPolytope{Float64,Array{Float64,1}},VPolytope{Float64,Array{Float64,1}},Missing}=missing,
    bipartiteWeylBasis::Union{Vector{Array{Complex{Float64},2}},Missing}=missing,
    dictionaries::Union{Any,Missing}=missing,
    mubSet::Union{Vector{Vector{Vector{ComplexF64}}},Missing}=missing,
    boundedEWs::Union{Array{BoundedCoordEW},Missing}=missing,
    precision=10,
    relUncertainity=0.0
)
```

Return an `AnalysedCoordState` for a `coordState` in `d` dimensions based on the given `anaSpec` and corresponding analysis objects.

If an entanglement check should not be carried out or if an analysis object in not passed as variable, the corresponding property in `anaSpec` needs to be `false`.  In this case, return the corresponding property of the `AnalysedCoordState` as `missing`.
