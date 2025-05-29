```
ETDRK4TimeStepper(equation::Equation, dt, dev::Device=CPU())
```

デバイス `dev` 上の `equation` に対して、タイムステップ `dt` を持つ4次指数時間差分ルンゲクッタタイムステッパーを構築します。
