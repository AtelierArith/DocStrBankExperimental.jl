```
EdererI
```

このメソッドは、次の推定を適用することによってネット生存確率を推定します：

$$
\partial\hat{\Lambda}_E(t) = \frac{\sum_i N_i(u)}{\sum_i Y_i(u)} - \frac{\sum_i S_{P_i}(u)d\Lambda_{P_i}(u)}{\sum_i S_{P_i}(u)}
$$

この関数を呼び出すには：

```
fit(EdererI, @formula(Surv(time,status)~covariable1 + covariable2), data, ratetable)
```
