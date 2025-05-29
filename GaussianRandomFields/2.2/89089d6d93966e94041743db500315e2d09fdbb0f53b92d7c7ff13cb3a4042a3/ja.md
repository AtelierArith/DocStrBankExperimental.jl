```
plot_eigenvalues(grf)
```

ガウスランダムフィールドの固有値のログ-ログプロット。`Spectral`、`KarhunenLoeve`、および `CirculantEmbedding` タイプのガウスランダムフィールドジェネレーターにのみ利用可能です。

# 例

```jldoctest
julia> cov = CovarianceFunction(2, Gaussian(.1))
2次元ガウス共分散関数 (λ=0.1, σ=1.0, p=2.0)

julia> pts = range(0, stop=1, length=51)
0.0:0.02:1.0

julia> grf = GaussianRandomField(cov, KarhunenLoeve(100), pts, pts)
2次元ガウス共分散関数 (λ=0.1, σ=1.0, p=2.0) を持つガウスランダムフィールド、51×51の構造化グリッド上で、100項のKL展開を使用

julia> plot_eigenvalues(grf);

```

関連情報: [`plot_eigenfunction`](@ref)
