```
function replace_subgraph(g::AbstractGraph, w::AbstractGraph, m::AbstractGraph)

`g`の修正されたコピーを作成し、サブグラフ`w`を新しいグラフ`m`で置き換えます。
ファインマン図の場合、サブグラフ`w`と`m`は同じ図のタイプ、順序、および外部インデックスを持っている必要があります。
```

# 引数:

  * `g::AbstractGraph`: 修正されるグラフ
  * `w::AbstractGraph`: 置き換えられるサブグラフ
  * `m::AbstractGraph`: 新しいサブグラフ
