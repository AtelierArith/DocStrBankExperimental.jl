```
fit(UnitRangeTransform, X; dims=nothing, unit=true)
```

ベクトルまたは行列 `X` にスケーリングパラメータをフィットさせ、`UnitRangeTransform` 変換オブジェクトを返します。

# キーワード引数

  * `dims`: `1` の場合、列方向に標準化パラメータをフィットさせます;

`2` の場合、行方向にフィットさせます。デフォルトは `nothing` です。

  * `unit`: `true`（デフォルト）であれば、最小データをゼロにシフトします。

# 例

```jldoctest
julia> using StatsBase

julia> X = [0.0 -0.5 0.5; 0.0 1.0 2.0]
2×3 Matrix{Float64}:
 0.0  -0.5  0.5
 0.0   1.0  2.0

julia> dt = fit(UnitRangeTransform, X, dims=2)
UnitRangeTransform{Float64, Vector{Float64}}(2, 2, true, [-0.5, 0.0], [1.0, 0.5])

julia> StatsBase.transform(dt, X)
2×3 Matrix{Float64}:
 0.5  0.0  1.0
 0.0  0.5  1.0
```
