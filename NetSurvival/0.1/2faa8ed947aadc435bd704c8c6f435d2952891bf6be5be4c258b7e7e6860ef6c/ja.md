```
PoharPerme
```

このメソッドは、次の推定を適用することによってネット生存確率を推定します：

$$
\partial\hat{\Lambda}_E(t) = \frac{\sum_i \frac{dN_i(u)}{S_{P_i}(u)} - \sum_i \frac{Y_i(u)}{S_{P_i}(u)}d\Lambda_{P_i}(u)}{\sum_i \frac{Y_i(u)}{S_{P_i}(u)}}
$$

特定のレートテーブルに基づいてデータにPohar Permeを適合させるには、以下の例をコードに適用してください：

```
fit(PoharPerme, @formula(Surv(time,status)~covariable1 + covariable2), data, ratetable)
```

参考文献：

  * [PoharPerme2012](@cite) Perme, Maja Pohar and Stare, Janez and Estève, Jacques (2012). On Estimation in Relative Survival.
