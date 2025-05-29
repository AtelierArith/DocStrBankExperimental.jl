```
Cholesky()
```

コバリアンス行列のコレスキー因子分解に基づいて[`GaussianRandomFieldGenerator`](@ref)を返します。

# 例

```jldoctest
julia> cov = CovarianceFunction(2, Matern(.3, 1))
2d Matérnコバリアンス関数 (λ=0.3, ν=1.0, σ=1.0, p=2.0)

julia> pts = range(0, stop=1, length=51) 
0.0:0.02:1.0

julia> grf = GaussianRandomField(cov, Cholesky(), pts, pts)
コレスキー分解を使用した51×51の構造化グリッド上の2d Matérnコバリアンス関数 (λ=0.3, ν=1.0, σ=1.0, p=2.0) を持つガウスランダムフィールド

julia> heatmap(grf);

```

!!! warning
    コレスキー因子分解は、コバリアンス行列が対称かつ正定値であることを要求します。コバリアンス行列が正定値でない場合、エラーが発生します。その場合は、`Spectral`メソッドを使用してみてください。


関連情報: [`Spectral`](@ref), [`KarhunenLoeve`](@ref), [`CirculantEmbedding`](@ref)
