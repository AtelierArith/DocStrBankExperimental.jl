```
sparseL(m::LinearMixedModel; fname::Symbol=first(fnames(m)), full::Bool=false)
```

下三角のコレスキー因子 `L` を `SparseMatrix{T,Int32}` として返します。

`full` は、固定効果および応答に関連する `L` の部分を含めるかどうかを示します。

`fname` は、含める最初のグルーピング因子を指定します。`fname` に対応するブロックの左側にあるブロックは削除されます。デフォルトは最初のもので、すなわち最も左のブロックであり、したがってすべてのブロックです。
