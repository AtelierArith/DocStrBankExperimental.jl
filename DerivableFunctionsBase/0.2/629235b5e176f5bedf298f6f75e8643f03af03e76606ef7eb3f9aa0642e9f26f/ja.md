```
GetMatrixJac(ADmode::Val, F::Function; kwargs...) -> Function
```

配列値関数 `F` のヤコビアンを指定されたバックエンドを介してアウトオブプレースで計算する関数を返します。

例:

```julia
Jacobian = GetMatrixJac(Val(:ForwardDiff), x->[x[1]^2 x[2]^3; x[1]*x[2] 2])
Jacobian(rand(2))
```

使用可能なバックエンドについては、`diff_backends()` を参照してください。
