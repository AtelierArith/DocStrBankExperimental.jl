```
LogLikeMLE(DM::DataModel) -> Real
```

最大尤度推定値で評価されたときの対数尤度 $\ell$ の値を返します。すなわち、$\ell(\mathrm{data} \, | \, \theta_\text{MLE})$ です。パフォーマンスの理由から、この値は `DataModel` 型の一部として保存されます。
