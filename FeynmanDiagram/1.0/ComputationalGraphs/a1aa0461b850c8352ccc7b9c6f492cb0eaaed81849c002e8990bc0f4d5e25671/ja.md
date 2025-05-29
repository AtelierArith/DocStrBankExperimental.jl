```
function remove_zero_valued_subgraphs(g::AbstractGraph)

ゼロ値（ゼロサブグラフファクター）のサブグラフを削除したグラフ `g` のコピーを返します。
すべてのサブグラフがゼロ値の場合、最初のもの（`eldest(g)`）が保持されます。
```

# 引数:

  * `g::AbstractGraph`: 修正されるグラフ
