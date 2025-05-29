```
PoharPerme
```

This method estimates net survival probabilities by applying the following estimation:

$$
\partial\hat{\Lambda}_E(t) = \frac{\sum_i \frac{dN_i(u)}{S_{P_i}(u)} - \sum_i \frac{Y_i(u)}{S_{P_i}(u)}d\Lambda_{P_i}(u)}{\sum_i \frac{Y_i(u)}{S_{P_i}(u)}}
$$

To fit the Pohar Perme to your data based on a certain rate table, apply the example below to your code : 

```
fit(PoharPerme, @formula(Surv(time,status)~covariable1 + covariable2), data, ratetable)
```

References: 

  * [PoharPerme2012](@cite) Perme, Maja Pohar and Stare, Janez and Estève, Jacques (2012). On Estimation in Relative Survival.
