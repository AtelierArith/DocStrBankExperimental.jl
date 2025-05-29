```
GetJac!(ADmode::Val, F::Function; kwargs...) -> Function
```

指定された `ADmode` によってバックエンドを介してヤコビアンをインプレースで計算する関数を返します。 `GetJac!` によって返される関数は、引数の構造が `(Y::AbstractMatrix, X::AbstractVector)` であり、`F` の `X` で評価されたヤコビアンが `Y` に保存されます。

例:

```julia
Jacobian! = GetJac!(Val(:ForwardDiff), x->[x[1]^2, -x[2]^3, x[1]*x[2]])
Y = Matrix{Float64}(undef, 3, 2)
Jacobian!(Y, rand(2))
```

使用可能なバックエンドについては、`diff_backends()` を参照してください。
