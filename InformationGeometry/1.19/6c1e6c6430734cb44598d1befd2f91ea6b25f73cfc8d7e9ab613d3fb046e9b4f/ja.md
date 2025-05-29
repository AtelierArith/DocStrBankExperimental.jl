```
PracticallyIdentifiable(P::ParameterProfiles) -> Real
```

与えられた `ParameterProfiles` のすべてのプロファイルが依然として実質的に同定可能である最大レベルを決定します。プロファイルに対して `IsCost=true` が選択された場合、出力はコスト関数値 `2(L_MLE - PL_i(θ))` の最大偏差です。代わりに `IsCost=false` が選択された場合、コスト関数の偏差はすでに信頼レベルに再スケーリングされているため、`PracticallyIdentifiable` の出力は、モデルが依然として実質的に同定可能である標準偏差 σ の単位での最大信頼レベルです。
