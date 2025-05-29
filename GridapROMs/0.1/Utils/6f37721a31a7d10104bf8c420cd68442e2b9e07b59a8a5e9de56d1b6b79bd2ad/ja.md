```
compute_relative_error(
  sol::AbstractArray{T,N},
  sol_approx::AbstractArray{T,N},
  args...
  ) where {T,N} -> Number
```

`sol` と `sol_approx` の相対誤差を計算します。デフォルトではユークリッドノルムで計算されます。異なるノルム（通常はスパース行列で表される）を引数として提供することができます。
