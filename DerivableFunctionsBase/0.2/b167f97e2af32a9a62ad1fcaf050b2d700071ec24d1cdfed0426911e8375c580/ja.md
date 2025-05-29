```
GetMatrixJac!(ADmode::Val, F::Function; kwargs...) -> Function
```

指定された `ADmode` によってバックエンドを介して配列値関数のヤコビ行列をインプレースで計算する関数を返します。 `GetMatrixJac!` によって返される関数は、引数の構造が `(Y::AbstractArray, X::AbstractVector)` であり、`X` で評価された `F` のヤコビ行列が `Y` に保存されます。

例:

```julia
Jacobian! = GetMatrixJac!(Val(:ForwardDiff), x->[x[1]^2 x[2]^3; x[1]*x[2] 2])
Y = Array{Float64}(undef, 2, 2, 2)
Jacobian!(Y, rand(2))
```

使用可能なバックエンドについては、`diff_backends()` を参照してください。
