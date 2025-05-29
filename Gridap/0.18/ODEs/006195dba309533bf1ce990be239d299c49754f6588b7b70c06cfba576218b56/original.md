```
solve(
  odeslvr::ODESolver, tfeop::TransientFEOperator,
  t0::Real, tF::Real, uhs0
) -> TransientFESolution
```

Create a `TransientFESolution` wrapper around the `TransientFEOperator` and `ODESolver`, starting at time `t0` with state `us0`, to be evolved until `tF`.
