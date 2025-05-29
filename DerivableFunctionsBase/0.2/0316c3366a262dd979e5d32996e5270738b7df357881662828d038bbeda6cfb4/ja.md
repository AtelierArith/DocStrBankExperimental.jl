```
GetDeriv(ADmode::Val, F::Function; kwargs...) -> Function
```

指定された `ADmode` によってバックエンドを介して `F` のスカラー導関数を計算する関数を返します。

例:

```julia
Derivative = GetDeriv(Val(:ForwardDiff), x->exp(-x^2))
Derivative(5.0)
```

利用可能なバックエンドについては `diff_backends()` を参照してください。
