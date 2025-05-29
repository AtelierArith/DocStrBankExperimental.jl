```
IntegrateOverApproxConfidenceRegion(DM::AbstractDataModel, Domain::HyperCube, sol::AbstractODESolution, F::Function; N::Int=Int(1e5), WE::Bool=true, kwargs...)
IntegrateOverApproxConfidenceRegion(DM::AbstractDataModel, Domain::HyperCube, Planes::AbstractVector{<:Plane}, sols::AbstractVector{<:AbstractODESolution}, F::Function; N::Int=Int(1e5), WE::Bool=true, kwargs...)
```

Integrates a function `F` over the intersection of `Domain` and the polygon defined by `sol`.
