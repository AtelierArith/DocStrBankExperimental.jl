```
sinkhorn_unbalanced(μ, ν, C, λ1::Real, λ2::Real, ε; kwargs...)
```

ソースとターゲットの周辺分布 `μ` と `ν`、サイズ `(length(μ), length(ν))` のコスト行列 `C`、エントロピー正則化パラメータ `ε`、および周辺緩和項 `λ1` と `λ2` を持つ非バランスエントロピー正則化最適輸送問題の最適輸送計画を計算します。

最適輸送計画 `γ` は `C` と同じサイズであり、次の問題を解決します。

$$
\inf_{\gamma} \langle \gamma, C \rangle
+ \varepsilon \Omega(\gamma)
+ \lambda_1 \operatorname{KL}(\gamma 1 | \mu)
+ \lambda_2 \operatorname{KL}(\gamma^{\mathsf{T}} 1 | \nu),
$$

ここで、$\Omega(\gamma) = \sum_{i,j} \gamma_{i,j} \log \gamma_{i,j}$ はエントロピー正則化項であり、$\operatorname{KL}$ はクルバック・ライブラー散逸です。

ここでサポートされているキーワード引数は、一般的なソフト周辺制約を持つ非バランス最適輸送問題の `sinkhorn_unbalanced` と同じです。 ```
