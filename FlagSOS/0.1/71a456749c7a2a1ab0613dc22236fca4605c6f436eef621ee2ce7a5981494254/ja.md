```
labelCanonically(F::QuantumFlag{T,R})::QuantumFlag{T,R} where {T <: Flag, R <: Real}
```

フラグ `F` を標準的にラベル付けします。2つのフラグが同型である場合、この関数は同じフラグを返すべきです。
