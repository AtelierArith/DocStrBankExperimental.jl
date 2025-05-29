```
chaikinvolatility(ta, n = 10, p = 10; h = High, l = :Low)
```

Chaikin Volatility

# Arguments

  * `n` is the smooth period
  * `p` is the previous period

# Formula

$$
\text{Chaikin Vola} =
  \frac{\text{EMA}(P^\text{High}_t - P^\text{Low}_t, n) - \text{EMA}(P^\text{High}_{t-p} - P^\text{Low}_{t-p}, n)}
       {\text{EMA}(P^\text{High}_{t-p} - P^\text{Low}_{t-p}, n)}
  \times 100
$$

# References

  * [IncredibleCharts](https://www.incrediblecharts.com/indicators/chaikin_volatility.php)
