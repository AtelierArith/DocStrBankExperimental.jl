```
LaplaceEM(model, Estep_optimizer = Optimizer(), derivative_threshold = 1e-3, iterations = 10, stopper = () -> false)
```

期待値最大化（EM）法をラプラス近似を用いて実装します。詳細は[Huys et al. (2012)](http://dx.doi.org/10.1371/journal.pcbi.1002410)を参照してください。
