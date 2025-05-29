```
changebonds(ψ::AbstractMPS, H, alg, envs) -> ψ′, envs′
changebonds(ψ::AbstractMPS, alg) -> ψ′
```

アルゴリズム `alg` を使用して `ψ` のボンド次元を変更し、新しい `ψ` と新しい `envs` を返します。

参照: [`SvdCut`](@ref), [`RandExpand`](@ref), [`VUMPSSvdCut`](@ref), [`OptimalExpand`](@ref)
