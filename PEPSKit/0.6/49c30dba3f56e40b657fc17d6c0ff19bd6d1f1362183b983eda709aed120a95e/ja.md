```
simpleupdate(peps::InfiniteWeightPEPS, H::LocalOperator, alg::SimpleUpdate;
             bipartite::Bool=false, check_interval::Int=500)
```

最近接隣接ハミルトニアン `H` を用いて単純更新を実行し、進化情報は `check_interval` ステップごとに印刷されます。

`bipartite == true` の場合（正方格子用）、単位セルサイズは `(2, 2)` と仮定され、対角線上で同じテンソルおよび x/y 重みが使用されます。すなわち、`(row, col)` と `(row+1, col+1)` で同じです。
