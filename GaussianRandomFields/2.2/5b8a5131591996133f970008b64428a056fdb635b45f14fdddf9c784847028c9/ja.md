```
sample(grf)
    sample(grf[, xi])
```

ガウス乱数場 `grf` から（オプションの）正規分布に従う乱数 `xi` を使用してサンプルを取得します。ベクトル `xi` は適切な長さでなければなりません。

# 例

```jldoctest
julia> cov = CovarianceFunction(2, Whittle(.1))
2d Whittle covariance function (λ=0.1, σ=1.0, p=2.0)

julia> pts = pts = range(0, stop=1, length=51)
0.0:0.02:1.0

julia> grf = GaussianRandomField(cov, CirculantEmbedding(), pts, pts)
Gaussian random field with 2d Whittle covariance function (λ=0.1, σ=1.0, p=2.0) on a 51×51 structured grid, using a circulant embedding

julia> sample(grf);

julia> sample(grf, xi=randn(randdim(grf)));
```

関連情報: [`GaussianRandomField`](@ref), [`Matern`](@ref), [`CovarianceFunction`](@ref), [`CirculantEmbedding`](@ref)
