```
GetDoubleJac(ADmode::Val, F::Function; kwargs...) -> Function
```

ベクトル値関数 `F` のヤコビアンのヤコビアンを、`ADmode` で指定されたバックエンドを介してアウトオブプレースで計算する関数を返します。

例:

```julia
DoubleJacobian = GetDoubleJac(Val(:ForwardDiff), x->[x[1]^2, x[1]*x[2]^3])
DoubleJacobian(rand(2))
```

使用可能なバックエンドについては、`diff_backends()` を参照してください。
