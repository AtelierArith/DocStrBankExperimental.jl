```
Histogram <: AbstractHistogram
```

`Histogram`型は、実数直線上の区間（*ビン*として知られる）に集計されたデータを表します。高次元の場合は、実空間においても同様です。ヒストグラムは、`fit`メソッドを使用してデータにフィットさせることができます。

# フィールド

  * edges: 各次元におけるビンの境界を含むイテレータ。
  * weights: 各ビンの重みを含む配列。
  * closed: ビン（半開区間またはそれに相当する高次元のもの）がどちら側で閉じられているかを示す`:right`または`:left`の値を持つシンボル。以下に例を示します。
  * isdensity: `Histogram`には2つの解釈があります。`isdensity=false`の場合、ビンの重みはビン内の量の合計に対応します。`isdensity=true`の場合、ビン内の量の密度（量 / 体積）に対応します。以下に例を示します。

# 例

## `closed`を示す例

```jldoctest
julia> using StatsBase

julia> fit(Histogram, [2.],  1:3, closed=:left)
Histogram{Int64, 1, Tuple{UnitRange{Int64}}}
edges:
  1:3
weights: [0, 1]
closed: left
isdensity: false

julia> fit(Histogram, [2.],  1:3, closed=:right)
Histogram{Int64, 1, Tuple{UnitRange{Int64}}}
edges:
  1:3
weights: [1, 0]
closed: right
isdensity: false
```

## `isdensity`を示す例

```jldoctest
julia> using StatsBase, LinearAlgebra

julia> bins = [0,1,7]; # 小さなビンと大きなビン

julia> obs = [0.5, 1.5, 1.5, 2.5]; # 小さなビンに1つ、大きなビンに3つの観測値

julia> h = fit(Histogram, obs, bins)
Histogram{Int64, 1, Tuple{Vector{Int64}}}
edges:
  [0, 1, 7]
weights: [1, 3]
closed: left
isdensity: false

julia> # isdensity = falseを観察し、weightsフィールドが各ビンの観測数を記録していることを確認

julia> normalize(h, mode=:density)
Histogram{Float64, 1, Tuple{Vector{Int64}}}
edges:
  [0, 1, 7]
weights: [1.0, 0.5]
closed: left
isdensity: true

julia> # isdensity = trueを観察し、weightsが各ビンサイズあたりの観測数を示していることを確認
```
