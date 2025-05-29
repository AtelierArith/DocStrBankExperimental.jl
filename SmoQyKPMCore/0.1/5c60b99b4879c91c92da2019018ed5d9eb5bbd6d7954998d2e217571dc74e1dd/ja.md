```
kpm_update_bounds!(
    kpm_expansion::KPMExpansion{T}, func::Function, bounds
) where {T<:AbstractFloat}
```

インプレースで[`KPMExpansion`](@ref)のインスタンスを更新し、固有スペクトル`bounds`の新しい値を反映させ、展開係数を再計算します。
