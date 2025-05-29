```
set!(prop, hdrs, i, value)
```

トレースプロパティ `prop::TraceProperty` の値を、`hdrs::Array{UInt8,2}` の i 番目の列のヘッダーに `value::T` として設定します。例えば、`io=jsopen("test.js"); hdrs=readframehdrs(io,1); set!(prop(io,"REC_X"), 1, 10.0)` のようになります。
