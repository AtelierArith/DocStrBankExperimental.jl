```julia
forcingOp(f, V, discr; f_update_func, f_update_func!)

```

演算子としての強制を追加しました。

F = forcingOp(f) L = A + F

F(u) = 0 * u + M * f L(u) = A * u + M * f
