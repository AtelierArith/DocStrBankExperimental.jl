```
changebonds(ψ::AbstractMPS, H, alg, envs) -> ψ′, envs′
changebonds(ψ::AbstractMPS, alg) -> ψ′
```

Change the bond dimension of `ψ` using the algorithm `alg`, and return the new `ψ` and the new `envs`.

See also: [`SvdCut`](@ref), [`RandExpand`](@ref), [`VUMPSSvdCut`](@ref), [`OptimalExpand`](@ref)
