```
GetHess!(ADmode::Val, F::Function; kwargs...) -> Function
```

指定されたバックエンドによってインプレースでヘッセ行列を計算する関数を返します。`GetHess!`によって返される関数は、引数の構造が`(Y::AbstractMatrix, X::AbstractVector)`であり、`X`で評価された`F`のヘッセ行列が`Y`に保存されます。

例:

```julia
Hessian! = GetHess!(Val(:ForwardDiff), x->x[1]^2 -x[2]^3 + x[1]*x[2])
Y = Matrix{Float64}(undef, 2, 2)
Hessian!(Y, rand(2))
```

使用可能なバックエンドについては、`diff_backends()`を参照してください。
