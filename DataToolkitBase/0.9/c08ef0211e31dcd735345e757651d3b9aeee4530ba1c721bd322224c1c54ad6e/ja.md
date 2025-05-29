```
@advise [source] f(args...; kwargs...)
```

関数呼び出し `f(args...; kwargs...)` を *advised* 関数呼び出しに変換します。このとき、アドバイスコレクションは `source` または `args` の最初のデータのような値から取得されます。

  * すなわち、`DataCollection`、`DataSet`、または `AbstractDataTransformer`

例えば、`@advise myfunc(other, somedataset, rest...)` は `somedataset.collection.advise(myfunc, other, somedataset, rest...)` と同等です。

このマクロはかなり小さなコード変換を行いますが、明確さを向上させるはずです。
