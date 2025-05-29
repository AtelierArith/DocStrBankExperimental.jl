```
convertvalue(T, x::LabeledArray)
```

`x` に含まれるデータ値の型を `T` に変換します。このメソッドは `convert(AbstractArray{LabeledValue{T, K}, N}}, x)` と同等です。
