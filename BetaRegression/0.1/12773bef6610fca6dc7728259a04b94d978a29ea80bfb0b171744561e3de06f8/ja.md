```
confint(model::BetaRegressionModel; level=0.95)
```

$$
p
$$

回帰係数を持つモデルについて、指定された `level` で推定された係数と精度の信頼区間の $(p + 1) \times 2$ 行列を返します。
