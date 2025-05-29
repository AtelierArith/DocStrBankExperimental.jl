```
supersaturation(param_set, q, ρ, T, Liquid())
supersaturation(param_set, q, ρ, T, Ice())
supersaturation(ts, Ice())
supersaturation(ts, Liquid())
```

  * `param_set` - 地球のパラメータを持つ抽象セット
  * `q` - 相分配
  * `ρ` - 空気密度
  * `T` - 空気温度
  * `Liquid()`, `Ice()` - 処理する液体または氷の相
  * `ts` - 熱力学的状態

水または氷に対する過飽和 (pv/pv_sat -1) を返します。
