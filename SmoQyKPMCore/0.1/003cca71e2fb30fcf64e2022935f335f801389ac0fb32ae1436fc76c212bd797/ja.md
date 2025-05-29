```
kpm_update_order!(
    kpm_expansion::KPMExpansion, func::Function, M::Int, N::Int = 2*M
)
```

インプレースで[`KPMExpansion`](@ref)のインスタンスの展開次数`M`を更新し、展開係数を再計算します。また、関数`func`が展開係数を計算するために評価される点の数`N`を更新することも可能です。
