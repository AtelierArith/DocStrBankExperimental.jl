```
GetJac(ADmode::Val, F::Function; kwargs...) -> Function
```

指定された `ADmode` によってバックエンドを介して `F` のヤコビ行列を計算する関数を返します。

例:

```julia
Jacobian = GetJac(Val(:ForwardDiff), x->[x[1]^2, -x[2]^3, x[1]*x[2]])
Jacobian(rand(2))
```

使用可能なバックエンドについては、`diff_backends()` を参照してください。
