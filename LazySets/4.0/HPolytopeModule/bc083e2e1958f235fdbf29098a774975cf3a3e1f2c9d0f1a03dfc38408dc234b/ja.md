# 拡張ヘルプ

```
rand(::Type{HPolytope}; [N]::Type{<:Real}=Float64, [dim]::Int=2,
     [rng]::AbstractRNG=GLOBAL_RNG, [seed]::Union{Int, Nothing}=nothing)
```

### 入力

  * `num_vertices` – （オプション、デフォルト: `-1`）多面体の頂点の数の上限（下記のコメントを参照）

### アルゴリズム

`num_vertices == 0` の場合、固定の非実現可能な多面体（`EmptySet` に対応）を作成します。

`num_vertices == 1` の場合、ランダムな `Singleton` を作成し、それを変換します。

`dim == 1` の場合、ランダムな `Interval` を作成し、それを変換します。

`dim == 2` の場合、ランダムな `VPolygon` を作成し、それを変換します。

それ以外の場合、ランダムな `VPolytope` を作成し、それを変換します（したがって、引数 `num_vertices` も）。[`rand(::Type{VPolytope})`](@ref) を参照してください。
