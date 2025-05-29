```
path_to_matrix(g::GridGraph, path::Vector{<:Integer})
```

グラフ `g` における最短の `s -> d` パスを、サイズ `height(g) * width(g)` の整数行列として格納します。ここで、エントリ `(i,j)` は関連する頂点への訪問回数をカウントします。
