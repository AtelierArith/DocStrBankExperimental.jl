`Matroid`を次のように作成します：

  * `Matroid(m::Int, r::AbstractRankFunction)` 要素の数とランク関数を指定します。
  * `Matroid(A::AbstractMatrix)` 行列を指定します。
  * `Matroid(g::Graph)` グラフを指定します。
  * `Matroid(g::EasyMultiGraph)` 多重グラフを指定します。
  * `Matroid()` は要素のないマトロイドを生成します。

また、`UniformMatroid`も参照してください。
