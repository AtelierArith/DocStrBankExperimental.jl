```
solve(
  odeslvr::ODESolver, odeop::ODEOperator,
  t0::Real, tF::Real, us0::Tuple{Vararg{AbstractVector}},
) -> ODESolution
```

Create an `ODESolution` wrapper around the `ODEOperator` and `ODESolver`, starting with state `us0` at time `t0`, to be evolved until `tF`.
