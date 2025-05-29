```
with_jacobian(f, x, OP, ad::ADSelector)
```

タプル `(f(x), J)` を返し、型 `OP` の乗法ヤコビアン演算子 `J` を持ちます。

例:

```julia
using AutoDiffOperators, LinearMaps
y, J = with_jacobian(f, x, LinearMap, ad)
y == f(x)
_, J_explicit = with_jacobian(f, x, Matrix, ad)
J * z_r ≈ J_explicit * z_r
z_l' * J ≈ z_l' * J_explicit
```

`OP` は [`LinearMaps.LinearMap`](https://github.com/JuliaLinearAlgebra/LinearMaps.jl) （または `LinearMaps.FunctionMap`）または `Matrix` である可能性があります。他の演算子タイプは、演算子タイプのために [`AutoDiffOperators.mulfunc_operator`](@ref) を特化させることでサポートできます。

`with_jacobian` のデフォルト実装は、（随伴）ベクトルとの `J` の（随伴）乗算を実装するために [`jvp_func`](@ref) と [`with_vjp_func`](@ref) を使用します。
