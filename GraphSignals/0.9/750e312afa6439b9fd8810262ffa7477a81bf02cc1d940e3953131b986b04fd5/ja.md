```
aggregate_index(sg; direction=:undirected, kind=:edge)
```

散発操作のためのインデックス構造を生成します。

# 引数

  * `sg::SparseGraph`: 参照グラフ。
  * `direction::Symbol`: 集約するために選択するエッジの方向。`:inward` と `:outward` のいずれかでなければなりません。
  * `kind::Symbol`: エッジまたは頂点に基づいて特徴を集約します。`:edge` と `:vertex` のいずれかでなければなりません。
