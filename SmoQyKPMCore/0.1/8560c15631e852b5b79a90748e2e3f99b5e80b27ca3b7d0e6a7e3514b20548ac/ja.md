```
kpm_update!(
    kpm_expansion::KPMExpansion{T}, func::Function, bounds, M::Int, N::Int = 2*M
) where {T<:AbstractFloat}
```

インプレースで[`KPMExpansion`](@ref)のインスタンスを更新し、固有スペクトル`bounds`、展開次数`M`、および展開係数を計算する際に展開された関数が評価されるポイントの数を反映させます。これには、展開係数の再計算が含まれます。
