```
GetGrad!(ADmode::Val, F::Function; kwargs...) -> Function
```

指定されたバックエンドによってインプレースで勾配を計算する関数を返します。`GetGrad!`によって返される関数は、引数の構造が`(Y::AbstractVector, X::AbstractVector)`であり、`X`で評価された`F`の勾配が`Y`に保存されます。

例:

```julia
Gradient! = GetGrad!(Val(:ForwardDiff), x->x[1]^2 - x[2]^3)
Y = Vector{Float64}(undef, 2)
Gradient!(Y, rand(2))
```

利用可能なバックエンドについては、`diff_backends()`を参照してください。
