```
random_walk(g, start, n=1)
```

与えられたグラフ `g` からランダムウォークサンプルを描画します。グラフ上の各エッジの重みは遷移確率に比例すると考えられます。

# 引数

  * `g`: グラフトポロジーを表すデータ。可能なタイプは

      * 隣接行列。
      * `FeaturedGraph` または `SparseGraph` オブジェクト。
  * `start::Int`: グラフ `g` 上のランダムウォークの開始点。
  * `n::Int`: ランダムウォークのステップ数。

# 使用法

```julia
julia> using GraphSignals

julia> adjm = [0 1 0 1 1;
               1 0 0 0 0;
               0 0 1 0 0;
               1 0 0 0 1;
               1 0 0 1 0];

julia> fg = FeaturedGraph(adjm);

julia> random_walk(adjm, 1)
1-element Vector{Int64}:
 5

julia> random_walk(fg, 1, 3)
3-element Vector{Int64}:
 5
 4
 4

julia> using Flux

julia> fg = fg |> gpu;

julia> random_walk(fg, 4, 3)
3-element Vector{Int64}:
 1
 1
 1
```

さらに [`neighbor_sample`](@ref) を参照してください。
