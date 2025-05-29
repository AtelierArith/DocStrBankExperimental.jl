```
plot_covariance_matrix(grf[, pts...])

ガウス乱数場 `grf` の共分散関数を（オプションの）点 `pts` で評価し、結果をプロットします。
```

# 例

```jldoctest
julia> cov = CovarianceFunction(2, Matern(.3, 1))
2d Matérn 共分散関数 (λ=0.3, ν=1.0, σ=1.0, p=2.0)

julia> pts = range(0, stop=1, length=11)
0.0:0.1:1.0

julia> grf = GaussianRandomField(cov, CirculantEmbedding(), pts, pts, minpadding=7)
2d Matérn 共分散関数 (λ=0.3, ν=1.0, σ=1.0, p=2.0) を持つガウス乱数場、11×11 の構造化グリッド上で、循環埋め込みを使用

julia> plot_covariance_matrix(grf);

julia> pts = range(0, stop=1, length=21)
0.0:0.05:1.0

julia> plot_covariance_matrix(grf, pts, pts);

```
