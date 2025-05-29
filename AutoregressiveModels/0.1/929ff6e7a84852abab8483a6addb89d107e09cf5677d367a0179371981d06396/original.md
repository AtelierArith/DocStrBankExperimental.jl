```
ARMAProcess(ars, mas, intercept=nothing)
```

Return an autoregressive–moving-average process $y_t$ defined as

$$
\left(1-\sum_{i=1}^p \rho_i L^i\right) = c + \left(1-\sum_{i=1}^q \varphi_i L^i\right) \varepsilon_t
$$

where $\{\rho_i\}_i$, $\{\varphi_i\}_i$ and $c$ are specified with `mas`, `ars` and `intercept` respectively; $L$ is the lag operator. Notice the *negative* sign associated with the moving-average terms.
