## `biconnected_components!`

この関数は、基になるグラフの双連結成分の数を返します。入力として無向グラフを期待します。

## 関数

  * `number = biconnected_components!(A::MatrixNetwork, articulation::Vector{Bool}, map::Vector{Int64})`

## 入力

  * `A`: 隣接行列。
  * `articulation`: 各要素が初期値falseのブール配列。
  * `map`: エッジの数と等しいサイズのベクター。

## 返り値

  * `cn`: グラフの双連結成分の数

## 例

A = load*matrix*network("biconnected*example") B = MatrixNetwork(A) number*of*components = biconnected*components!(B, zeros(Bool,0), zeros(Int64,0))
