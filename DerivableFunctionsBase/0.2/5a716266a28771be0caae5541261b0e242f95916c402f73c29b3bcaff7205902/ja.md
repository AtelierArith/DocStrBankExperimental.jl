```
GetGrad(ADmode::Val, F::Function; kwargs...) -> Function
```

指定された `ADmode` によってバックエンドを介して `F` の勾配を計算する関数を返します。

例:

```julia
Gradient = GetGrad(Val(:ForwardDiff), x->x[1]^2 - x[2]^3)
Gradient(rand(2))
```

使用可能なバックエンドについては `diff_backends()` を参照してください。
