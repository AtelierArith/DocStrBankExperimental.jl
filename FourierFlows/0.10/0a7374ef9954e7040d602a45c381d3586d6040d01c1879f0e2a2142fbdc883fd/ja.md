```
FilteredRK4TimeStepper(equation::Equation, dev::Device=CPU(); filterkwargs...)
```

デバイス `dev` 上の `equation` に対してスペクトルフィルタリングを用いた4次5段2ストレージのルンゲ・クッタタイムステッパーを構築します。
