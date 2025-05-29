```
struct RobustMADS{Tmesh,Tsearch,Tpoll,Tkernel} <: AbstractMADS
    mesh::Tmesh
    search::Tsearch
    poll::Tpoll
    kernel::Tkernel
    cache::Cache
    f::Vector{Float64}
    P::Vector{Float64}
```
