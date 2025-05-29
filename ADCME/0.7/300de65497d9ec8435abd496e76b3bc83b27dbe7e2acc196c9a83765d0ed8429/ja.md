```
load_op_and_grad(oplibpath::Union{PyObject, String}, opname::String; multiple::Bool=false)
```

ライブラリ `oplibpath` から演算子 `opname` をロードします。勾配もインポートされます。 `multiple` が true の場合、演算子は複数の出力を持つと仮定されます。
