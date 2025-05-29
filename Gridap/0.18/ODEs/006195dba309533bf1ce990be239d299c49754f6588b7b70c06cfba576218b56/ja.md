```
solve(
  odeslvr::ODESolver, tfeop::TransientFEOperator,
  t0::Real, tF::Real, uhs0
) -> TransientFESolution
```

`TransientFESolution`を`TransientFEOperator`と`ODESolver`の周りにラップし、状態`us0`で`t0`から始めて`tF`まで進化させます。
