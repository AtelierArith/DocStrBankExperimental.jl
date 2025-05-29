```julia
struct Branch{Tkind, Tprob, T<:Union{BifurcationKit.ContResult, Vector{BifurcationKit.ContResult}}, Tbp} <: BifurcationKit.AbstractResult{Tkind, Tprob}
```

A Branch is a structure which encapsulates the result of the computation of a branch bifurcating from a bifurcation point.

  * `γ::Union{BifurcationKit.ContResult, Vector{BifurcationKit.ContResult}}`: Set of branches branching off the bifurcation point `bp`
  * `bp::Any`: Bifurcation point. It is thought as the root of the branches in γ
