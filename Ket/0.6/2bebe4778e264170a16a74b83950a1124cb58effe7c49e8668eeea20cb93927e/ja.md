```
discrimination_min_error(
    ρ::Vector{<:AbstractMatrix},
    q::Vector{<:Real} = fill(1/length(ρ), length(ρ));
    verbose = false,
    dualize = false,
    solver = Hypatia.Optimizer
)
```

状態のベクトル `ρ` を確率 `q` で識別する際の最小誤り確率と最適なPOVMを計算します。`q` が省略された場合は均一であると仮定されます。
