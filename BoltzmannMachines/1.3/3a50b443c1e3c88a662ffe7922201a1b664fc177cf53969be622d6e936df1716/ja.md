```
joindbms(dbms)
joindbms(dbms, visibleindexes)
```

ベクトル `dbms` で指定された DBM を、各 RBM の層を結合することによって結合します。モデルを相互接続する重みはゼロで初期化されます。

ベクトル `visibleindexes` が指定されている場合、それは i 番目の `dbms` の可視ノードの位置を結合された DBM で決定するインデックスベクトルを i 番目のエントリに含むことが期待されます。デフォルトでは、可視ノードのインデックスは連続していると仮定されます。
