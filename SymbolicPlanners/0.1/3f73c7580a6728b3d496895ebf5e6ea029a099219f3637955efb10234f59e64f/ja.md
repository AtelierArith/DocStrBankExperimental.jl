```julia
precompute!(h, domain, state, spec)

```

ドメイン、状態、および仕様に基づいてヒューリスティック情報を事前計算します。この関数は通常、[`Planner`](@ref)の探索アルゴリズムの初期化フェーズ中に1回呼び出されます。
