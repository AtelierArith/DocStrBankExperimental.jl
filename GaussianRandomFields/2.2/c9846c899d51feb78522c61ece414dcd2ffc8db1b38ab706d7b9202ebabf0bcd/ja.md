```
plot_eigenfunction(grf, n)
```

ガウス乱数場の`n`番目の固有関数の等高線プロット。`Spectral`および`KarhunenLoeve`タイプのガウス乱数場生成器のみで利用可能です。

# 例

```jldoctest
julia> cov = CovarianceFunction(2, Gaussian(.1))
2次元ガウス共分散関数 (λ=0.1, σ=1.0, p=2.0)

julia> pts = range(0, stop=1, length=51)
0.0:0.02:1.0

julia> grf = GaussianRandomField(cov, KarhunenLoeve(100), pts, pts)
2次元ガウス共分散関数 (λ=0.1, σ=1.0, p=2.0) を持つガウス乱数場、51×51の構造化グリッド上で、100項のKL展開を使用

julia> plot_eigenfunction(grf, 6); # 6番目の固有関数

```

参照: [`plot_eigenfunction`](@ref)
