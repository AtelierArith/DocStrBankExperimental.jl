```
BasisFunction{B <: AbstractBSplineBasis, T}
```

Describes a single basis function.

The basis function may belong to a [`BSplineBasis`](@ref) (in which case it's effectively a B-spline), or to a basis derived from a B-spline basis (such as a `RecombinedBSplineBasis`).

---

```
BasisFunction(basis::AbstractBSplineBasis, i::Int, [T = Float64])
```

Construct i-th basis function of the given basis.

The constructed function can be evaluated as `b(x)`, returning a value of type `T`.

---

```
(b::BasisFunction)(x, [op::AbstractDifferentialOp])
```

Evaluate basis function at coordinate `x`.

To evaluate a derivative, pass `Derivative(n)` as the `op` argument, with `n` the derivative order.

To evaluate multiple derivatives, pass a derivative range `Derivative(m:n)`. In particular, `Derivative(m:n)` evaluates the basis function itself and its first `n` derivatives.

More general differential operators, such as `Derivative(n) + λ Derivative(m)`, are also supported.
