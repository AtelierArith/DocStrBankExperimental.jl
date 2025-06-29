```
Ainv = get_nrminv(pedlist, f; rank=0)
Ainv = get_nrminv(pedlist; f, rank=0)
```

「ヘンダーソンの」方法を使用して、系譜リスト `pedlist` と近親交配係数 `f` から分子（加法的）関係行列の逆行列を計算します。`f` がない場合、この関数はすべての個体に対して近親交配がゼロであると仮定します。詳細については、Henderson (1976) および Quaas (1976) を参照してください。出力は、`f` と同じ型の要素を持つ SparseMatrixCSC であり、SparseMatrixDict（すなわち、ハッシュ行列）が一時的な行列として使用されます。Aの逆行列のサイズを固定したい場合は、`rank` を指定してください。この関数は、`rank` または系譜内の最大IDのいずれか大きいサイズで逆行列を作成します。
