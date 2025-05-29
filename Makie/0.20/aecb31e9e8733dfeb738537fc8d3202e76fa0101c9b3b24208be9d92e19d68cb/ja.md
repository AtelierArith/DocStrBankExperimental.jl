```
hexbin(xs, ys; kwargs...)
```

観測値 `xs` と `ys` のための六角形ビンを持つヒートマップをプロットします。

## 属性

### `Hexbin` に特有

  * `weights = nothing`: 各観測値の重み。`nothing`（各観測値は重み1を持つ）または任意の `AbstractVector{<: Real}` または `StatsBase.AbstractWeights` であることができます。
  * `bins = 20`: `Int` の場合、x および y 方向のビンの数を設定します。`Tuple{Int, Int}` の場合、x と y のビンの数を別々に設定します。
  * `cellsize = nothing`: `Real` の場合、幅 `cellsize` の等辺六角形を作成します。`Tuple{Real, Real}` の場合、六角形の幅と高さを別々に指定します。
  * `threshold::Int = 1`: 表示されるビン内の最小観測数。0 の場合、データの制限に収まるすべてのゼロカウントの六角形が表示されます。
  * `colorscale = identity`: ビン内の観測数をスケーリングする関数、例えば log10。

### 一般的

  * `colormap::Union{Symbol, Vector{<:Colorant}} = :viridis`
  * `colorrange::Tuple(<:Real,<:Real} = Makie.automatic`  `colormap` の開始点と終了点を表す値を設定します。
