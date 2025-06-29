```
node2vec(g; walks_per_node, len, p, q, dims)
```

グラフ `g` のノード埋め込み行列をサイズ (`nv(g)`, `dims`) で返します。グラフ上でノード埋め込みを計算します。グラフ上でバイアス付きランダムウォークを実行し、そのランダムウォークを文として扱うことで単語埋め込みを計算します。

# 引数

  * `g::FeaturedGraph`: ランダムウォークを実行するグラフ。
  * `walks_per_node::Int`: 各ノードから始まるウォークの数。総ウォーク数は `nv(g) * walks_per_node`
  * `len::Int`: ランダムウォークの長さ
  * `p::Real`: リターンパラメータ。ウォーク中にノードを即座に再訪する可能性を制御します。
  * `q::Real`: インアウトパラメータ。検索が内向きノードと外向きノードを区別できるようにします。
  * `dims::Int`: ベクトル次元の数
