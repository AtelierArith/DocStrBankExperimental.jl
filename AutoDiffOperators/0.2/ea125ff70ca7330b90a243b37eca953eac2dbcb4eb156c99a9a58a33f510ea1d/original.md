```
with_jacobian(f, x, OP, ad::ADSelector)
```

Returns a tuple `(f(x), J)` with a multiplicative Jabobian operator `J` of type `OP`.

Example:

```julia
using AutoDiffOperators, LinearMaps
y, J = with_jacobian(f, x, LinearMap, ad)
y == f(x)
_, J_explicit = with_jacobian(f, x, Matrix, ad)
J * z_r ≈ J_explicit * z_r
z_l' * J ≈ z_l' * J_explicit
```

`OP` may be [`LinearMaps.LinearMap`](https://github.com/JuliaLinearAlgebra/LinearMaps.jl) (resp. `LinearMaps.FunctionMap`) or `Matrix`. Other operator types can be supported by specializing [`AutoDiffOperators.mulfunc_operator`](@ref) for the operator type.

The default implementation of `with_jacobian` uses [`jvp_func`](@ref) and [`with_vjp_func`](@ref) to implement (adjoint) multiplication of `J` with (adjoint) vectors.
