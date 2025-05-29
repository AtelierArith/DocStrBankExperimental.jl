```
    (graph,cref)=graph_denman_beavers(k;T=ComplexF64,cref_mode=0)
```

行列の平方根に対するデンマン–ビーバーズ反復に対応するグラフを作成し、k 回の反復を使用します。キーワード引数 `cref_mode` は、すべての X と Y への参照（`cref_mode=0`）を保存するか、Y のみ（`cref_mode=-1`）を保存するか、または X のみ（`cref_mode=1`）を保存するかを指定します。

**参考文献**

1. E. Denman と A. Beavers. "行列の符号関数とシステムにおける計算". Applied Mathematics and Computation, 2(1), 1976. DOI: [10.1016/0096-3003(76)90020-5](https://doi.org/10.1016/0096-3003(76)90020-5)
