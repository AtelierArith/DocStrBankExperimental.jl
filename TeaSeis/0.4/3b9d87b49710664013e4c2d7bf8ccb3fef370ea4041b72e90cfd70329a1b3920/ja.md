```
prop(io, propertyname[, proptype=Any])
```

`io::JSeis` からトレースプロパティを取得します。ここで `propertyname` は `String` または `TracePropertyDef` のいずれかです。`propertyname` が `String` の場合、このメソッドは型不安定な結果を生成します。例えば：

```julia
io = jsopen("data.js")
p = prop(io, "REC_X")            # `String` を使用しているため、prop の出力型は推論されません
p = prop(io, "REC_X", Float32)   # `String` を使用しているため、prop の出力型は Float32 を使用して推論されます
p = prop(io, stockprop[:REC_X])  # `TracePropertyDef` を使用しているため、prop の出力型は推論されます
```

上記の例では、文字列 "REC*X" はシンボル `REC*X` に置き換えることができます。
