```julia
random_field(setup; ...) -> Any
random_field(setup, t; A, kp, psolver, rng) -> Any

```

ランダムフィールドを作成します。[Orlandi2000](@cite)のように。

  * `A`: 渦振幅スケーリング
  * `kp`: ピークエネルギー波数
