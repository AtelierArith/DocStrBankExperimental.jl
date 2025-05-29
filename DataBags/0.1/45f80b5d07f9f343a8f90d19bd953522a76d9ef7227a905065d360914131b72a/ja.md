```
wrap(T::Type{<:AbstractDataBag}, arg) -> obj::T
```

引数 `arg` を型 `T` のデータバッグにラップします。返されるオブジェクトは `arg` とその内容を共有します。

このメソッドは、辞書を複製することなく既存の辞書からデータバッグを構築するために使用できます。例として：

```
dict = Dict{Symbol,Any}(:a => 1, :foo => "bar")
cont = wrap(DataBag, dict)
cont.b = 33
dict["b"] == 33 # yields `true`
```

`wrap(DataBag, dict)` の文を `DataBag(dict)` に置き換えると、最後の文の結果は `false` になります。
