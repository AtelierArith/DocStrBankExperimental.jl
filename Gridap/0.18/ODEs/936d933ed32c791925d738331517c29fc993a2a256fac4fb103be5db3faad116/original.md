```
jacobian(
  odeop::ODEOperator,
  t::Real, us::Tuple{Vararg{AbstractVector}}, ws::Tuple{Vararg{Real}},
  odeopcache
) -> AbstractMatrix
```

Allocate a jacobian matrix for the `ODEOperator` and compute the jacobian of the residual of the `ODEOperator` with respect to all time derivatives, weighted by some factors `ws`.

The weights are ordered by increasing order of time derivative, i.e. the first weight corresponds to `∂residual / ∂u` and the last to `∂residual / ∂(d^N u / dt^N)`.
