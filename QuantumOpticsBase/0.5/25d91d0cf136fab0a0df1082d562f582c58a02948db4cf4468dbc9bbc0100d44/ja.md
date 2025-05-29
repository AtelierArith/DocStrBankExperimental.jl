```
時間依存和 (lazysum, coeffs, init_time)
時間依存和(::Type{Tf}, basis_l, basis_r; init_time=0.0)
時間依存和([::Type{Tf},] [basis_l,] [basis_r,] coeffs, operators; init_time=0.0)
時間依存和([::Type{Tf},] coeff1=>op1, coeff2=>op2, ...; init_time=0.0)
時間依存和(::Tuple, op::時間依存和)

時間依存係数を持つ演算子の遅延和。[`LazySum`](@ref) `lazysum`をラップし、`current_time`（または演算子の「時計」）と、時間の関数（または数値）として時間係数を指定する手段を追加します。

係数の型 `Tf` は明示的に指定できます。時間依存係数は評価時にこの型に変換されます。
```
