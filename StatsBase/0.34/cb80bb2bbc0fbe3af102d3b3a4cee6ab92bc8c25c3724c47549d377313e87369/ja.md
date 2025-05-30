```
fit(ZScoreTransform, X; dims=nothing, center=true, scale=true)
```

ベクトルまたは行列 `X` に標準化パラメータをフィットさせ、`ZScoreTransform` 変換オブジェクトを返します。

# キーワード引数

  * `dims`: `1` の場合、列方向に標準化パラメータをフィットさせます。`2` の場合、行方向にフィットさせます。デフォルトは `nothing` で、これは `dims=2` と同等ですが、非推奨の警告が表示されます。
  * `center`: `true`（デフォルト）の場合、データを中心化して平均をゼロにします。
  * `scale`: `true`（デフォルト）の場合、データをスケールして分散を1にします。

# 例

```jldoctest
julia> using StatsBase

julia> X = [0.0 -0.5 0.5; 0.0 1.0 2.0]
2×3 Matrix{Float64}:
 0.0  -0.5  0.5
 0.0   1.0  2.0

julia> dt = fit(ZScoreTransform, X, dims=2)
ZScoreTransform{Float64, Vector{Float64}}(2, 2, [0.0, 1.0], [0.5, 1.0])

julia> StatsBase.transform(dt, X)
2×3 Matrix{Float64}:
  0.0  -1.0  1.0
 -1.0   0.0  1.0
```
