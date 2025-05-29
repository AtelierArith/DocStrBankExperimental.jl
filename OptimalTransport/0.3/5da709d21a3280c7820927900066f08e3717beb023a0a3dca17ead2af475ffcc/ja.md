```
sinkhorn_unbalanced2(μ, ν, C, λ1, λ2, ε; plan=nothing, kwargs...)
sinkhorn_unbalanced2(μ, ν, C, proxdivF1!, proxdivF2!, ε; plan=nothing, kwargs...)
```

ソースとターゲットの周辺分布 `μ` と `ν`、コスト行列 `C` のサイズ `(length(μ), length(ν))`、エントロピー正則化パラメータ `ε`、および周辺緩和項 `λ1` と `λ2` または "proxdiv" 関数 `proxdivF1!` と `proxdivF2!` を用いたソフト周辺制約を持つ不均衡エントロピー正則化最適輸送問題の最適輸送計画を計算します。

事前に計算された最適輸送 `plan` を提供することができます。ここでサポートされている他のキーワード引数は、一般的なソフト周辺制約を持つ不均衡最適輸送問題のための [`sinkhorn_unbalanced`](@ref) と同じです。

参照: [`sinkhorn_unbalanced`](@ref)
