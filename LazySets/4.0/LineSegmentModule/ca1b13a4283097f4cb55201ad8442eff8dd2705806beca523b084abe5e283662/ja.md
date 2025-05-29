```
LineSegment{N, VN<:AbstractVector{N}} <: AbstractZonotope{N}
```

2Dの2点$p$と$q$の間の線分を表す型です。

### フィールド

  * `p` – 最初の点
  * `q` – 2番目の点

### 例

$$
x = y
$$

対角線に沿った線分：

```jldoctest linesegment_constructor
julia> s = LineSegment([0., 0], [1., 1.])
LineSegment{Float64, Vector{Float64}}([0.0, 0.0], [1.0, 1.0])

julia> dim(s)
2
```

`plot(s)`を使用して、`s`の端点とそれらを結ぶ線分をプロットします。端点を削除したい場合は、オプション`markershape=:none`と`seriestype=:shape`を渡します。

メンバーシップは∈（`in`）でチェックされます：

```jldoctest linesegment_constructor
julia> [0., 0] ∈ s && [.25, .25] ∈ s && [1., 1] ∈ s && [.5, .25] ∉ s
true
```

別の線分との交差が空であるかどうかを確認し、オプションで証人（この場合は唯一の共通点）を計算できます：

```jldoctest linesegment_constructor
julia> sn = LineSegment([1., 0], [0., 1.])
LineSegment{Float64, Vector{Float64}}([1.0, 0.0], [0.0, 1.0])

julia> isdisjoint(s, sn)
false

julia> isdisjoint(s, sn, true)
(false, [0.5, 0.5])
```
