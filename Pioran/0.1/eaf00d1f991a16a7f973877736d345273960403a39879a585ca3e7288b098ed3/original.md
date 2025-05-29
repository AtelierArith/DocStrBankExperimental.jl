```
CARMA(p, q, rα, β, σ²)
```

Continuous-time AutoRegressive Moving Average (CARMA) model for the power spectral density

  * `p`: the order of the autoregressive polynomial
  * `q`: the order of the moving average polynomial
  * `rα`: roots of the autoregressive polynomial length p+1
  * `β`: the moving average coefficients length q+1
  * `σ²`: the variance of the process

The power spectral density of the CARMA model is given by:

$$
\mathcal{P}(f) = \sigma^2 \left|\dfrac{\sum\limits_{k=0}^q \beta_k \left(2\pi\mathrm{i}f\right)^k }{\sum\limits_{l=0}^p \alpha_l \left(2\pi\mathrm{i}f\right)^l}\right|^2
$$
