```
solve(
  odeslvr::ODESolver, odeop::ODEOperator,
  t0::Real, tF::Real, us0::Tuple{Vararg{AbstractVector}},
) -> ODESolution
```

`ODEOperator` と `ODESolver` の周りに `ODESolution` ラッパーを作成し、時間 `t0` で状態 `us0` から始めて、`tF` まで進化させます。
