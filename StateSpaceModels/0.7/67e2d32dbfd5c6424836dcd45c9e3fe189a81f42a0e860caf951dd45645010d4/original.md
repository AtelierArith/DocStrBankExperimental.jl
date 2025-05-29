```
MultivariateBasicStructural(y::Matrix{Fl}, s::Int) where Fl
```

An implementation of a non-homogeneous seemingly unrelated time series equations for basic structural state-space model consists of trend (local linear trend) and seasonal components. It is defined by:

$$
\begin{gather*}
    \begin{aligned}
    y_{t} &=  \mu_{t} + \gamma_{t} + \varepsilon_{t} \quad &\varepsilon_{t} \sim \mathcal{N}(0, \Sigma_{\varepsilon})\\
    \mu_{t+1} &= \mu_{t} + \nu_{t} + \xi_{t} \quad &\xi_{t} \sim \mathcal{N}(0, \Sigma_{\xi})\\
    \nu_{t+1} &= \nu_{t} + \zeta_{t} \quad &\zeta_{t} \sim \mathcal{N}(0, \Sigma_{\zeta})\\
    \gamma_{t+1} &= -\sum_{j=1}^{s-1} \gamma_{t+1-j} + \omega_{t} \quad & \omega_{t} \sim \mathcal{N}(0, \Sigma_{\omega})\\
    \end{aligned}
\end{gather*}
$$

# Example

```jldoctest
julia> model = MultivariateBasicStructural(rand(100, 2), 12)
MultivariateBasicStructural
```

# References

  * Durbin, James, & Siem Jan Koopman. (2012). "Time Series Analysis by State Space Methods: Second Edition." Oxford University Press.
