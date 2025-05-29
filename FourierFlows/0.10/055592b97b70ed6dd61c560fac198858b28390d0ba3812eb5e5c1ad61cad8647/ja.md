```
FilteredAB3TimeStepper(equation::Equation, dev::Device=CPU(); filterkwargs...)
```

デバイス `dev` 上の `equation` に対してスペクトルフィルタリングを用いた3次アダムス-バッシュフォースタイムステッパーを構築します。
