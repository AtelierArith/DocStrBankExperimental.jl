```
FilteredRK4TimeStepper(equation::Equation, dev::Device=CPU(); filterkwargs...)
```

デバイス `dev` 上の `equation` に対してスペクトルフィルタリングを用いた4次ルンゲクッタタイムステッパーを構築します。
