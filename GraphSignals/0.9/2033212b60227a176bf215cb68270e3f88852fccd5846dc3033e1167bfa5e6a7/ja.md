```
neighbor_sample(g, start, n=1; replace=false)
```

与えられたグラフ `g` から隣接ノードのランダムサンプルを抽出します。グラフ上の各エッジの重みは遷移確率に比例すると考えられます。

# 引数

  * `g`: グラフトポロジーを表すデータ。可能なタイプは

      * 隣接行列。
      * `FeaturedGraph` または `SparseGraph` オブジェクト。
  * `start::Int`: グラフ `g` におけるランダム隣接ノードサンプリングのための頂点。
  * `n::Int`: ランダム隣接ノードサンプリングの数。
  * `replace::Bool`: 置換ありでサンプルするかどうか。

# 使用法

```julia
julia> using GraphSignals

julia> adjm = [0 1 0 1 1;
               1 0 0 0 0;
               0 0 1 0 0;
               1 0 0 0 1;
               1 0 0 1 0];

julia> fg = FeaturedGraph(adjm);

julia> neighbor_sample(adjm, 1)
1-element Vector{Int64}:
 4

julia> neighbor_sample(fg, 1, 3)
3-element Vector{Int64}:
 5
 4
 2

julia> using Flux

julia> fg = fg |> gpu;

julia> neighbor_sample(fg, 4, 3, replace=true)
3-element Vector{Int64}:
 1
 5
 5
```

詳細は [`random_walk`](@ref) を参照してください。
