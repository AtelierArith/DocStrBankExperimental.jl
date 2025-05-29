```
solve(prob::PricingProblem, method::LSM)
```

最小二乗モンテカルロ法を使用してアメリカンオプションの価格を算出します。

# 引数

  * `prob`: アメリカン `VanillaOption` を含む `PricingProblem`。
  * `method`: `LSM` 価格算出方法。

# 戻り値

  * 価格と停止戦略を含む `LSMSolution`。
