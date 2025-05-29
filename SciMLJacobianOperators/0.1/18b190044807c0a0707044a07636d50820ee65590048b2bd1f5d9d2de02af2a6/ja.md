```
StatefulJacobianOperator(jac_op::JacobianOperator, u, p)
```

[`JacobianOperator`](@ref) のラッパーで、入力 `u` と `p` を保存し、VJP と JVP を計算するための `mul!` と `*` を定義します。
