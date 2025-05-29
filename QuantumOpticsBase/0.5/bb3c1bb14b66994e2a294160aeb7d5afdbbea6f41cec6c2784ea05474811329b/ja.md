```
displace_analytical!(op, alpha::Number)
```

FockBasis 演算子 `op` の行列要素をその場で上書きし、`displace_analytical(eltype(op), basis(op), alpha)` と等しくなるようにします。
