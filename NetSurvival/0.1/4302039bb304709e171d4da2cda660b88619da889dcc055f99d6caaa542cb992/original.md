```
EdererII
```

This method estimates net survival probabilities by applying the following estimation:

$$
\partial\hat{\Lambda}_E(t) = \frac{\sum_i N_i(u)}{\sum_i Y_i(u)} - \frac{\sum_i Y_i(u)d\Lambda_{P_i}(u)}{\sum_i Y_i(u)}
$$

To call this function: 

```
fit(EdererII, @formula(Surv(time,status)~covariable1 + covariable2), data, ratetable)
```
