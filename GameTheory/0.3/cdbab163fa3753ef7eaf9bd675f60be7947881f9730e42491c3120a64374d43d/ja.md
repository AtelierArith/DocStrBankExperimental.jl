```
BROptions
```

`best_response`のオプションを含む構造体。

# フィールド

  * `tol::Real=1e-8` : 許容誤差レベル。
  * `tie_breaking::Symbol=:smallest` : `:smallest`または`:random`。
  * `rng::AbstractRNG=GLOBAL_RNG` : 擬似乱数生成器。
