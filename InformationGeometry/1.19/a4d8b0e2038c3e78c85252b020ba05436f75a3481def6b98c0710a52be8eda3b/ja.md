```
IntegrateOverApproxConfidenceRegion(DM::AbstractDataModel, Domain::HyperCube, sol::AbstractODESolution, F::Function; N::Int=Int(1e5), WE::Bool=true, kwargs...)
IntegrateOverApproxConfidenceRegion(DM::AbstractDataModel, Domain::HyperCube, Planes::AbstractVector{<:Plane}, sols::AbstractVector{<:AbstractODESolution}, F::Function; N::Int=Int(1e5), WE::Bool=true, kwargs...)
```

関数 `F` を `Domain` と `sol` によって定義された多角形の交差部分上で統合します。
