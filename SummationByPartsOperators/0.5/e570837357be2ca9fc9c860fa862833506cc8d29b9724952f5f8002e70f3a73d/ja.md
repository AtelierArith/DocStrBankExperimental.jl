```
mul_transpose_derivative_right!(u, D::DerivativeOperator, der_order::Val{N}, α=true, β=false)
```

グリッド関数 `u` を `α` 倍の転置された `N` 次導関数関数が `u` に適用されたものに加え、`β` 倍の `u` に設定します。これは、グリッドの右境界における `N` 次導関数関数の定義域内で行われます。したがって、係数 `α, β` は [`mul!`](@ref) と同じ意味を持ちます。
