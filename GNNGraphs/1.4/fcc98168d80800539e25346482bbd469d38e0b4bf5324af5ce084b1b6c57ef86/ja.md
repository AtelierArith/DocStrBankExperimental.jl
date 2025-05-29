```
color_refinement(g::GNNGraph, [x0]) -> x, num_colors, niters
```

グラフ彩色のための色の洗練アルゴリズム。グラフ `g` と初期彩色 `x0` が与えられたとき、アルゴリズムは固定点に達するまで彩色を反復的に洗練します。

各反復で、アルゴリズムは彩色のハッシュと各ノードの隣接ノードの色のソートされたリストを計算します。このハッシュは、彩色が変更されたかどうかを判断するために使用されます。

`math x_i' = hashmap((x_i, sort([x_j for j \in N(i)]))).``

このアルゴリズムは、グラフ同型性テストのための1-Weisfeiler-Lehmanアルゴリズムに関連しています。

# 引数

  * `g::GNNGraph`: 彩色するグラフ。
  * `x0::AbstractVector{<:Integer}`: 初期彩色。提供されない場合、すべてのノードは1で彩色されます。

# 戻り値

  * `x::AbstractVector{<:Integer}`: 最終的な彩色。
  * `num_colors::Int`: 使用された色の数。
  * `niters::Int`: 収束までの反復回数。
