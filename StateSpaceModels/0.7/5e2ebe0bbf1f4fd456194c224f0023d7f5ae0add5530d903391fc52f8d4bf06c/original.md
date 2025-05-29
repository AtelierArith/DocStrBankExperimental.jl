```
DAR(y::Vector{Fl}, lags::Int) where Fl
```

A Dynamic Autorregressive model is defined by:

$$
\begin{gather*}
    \begin{aligned}
        y_{t} &= \phi_0 + \sum_{i=1}^{lags} \phi_{i, t} y_{t - i} + \varepsilon_{t}  \quad \varepsilon_{t} \sim \mathcal{N}(0, \sigma^2_{\varepsilon})\\
        \phi_{i, t+1} &= \phi_{i, t} + \eta{i, t}  \quad \eta{i, t} \sim \mathcal{N}(0, \sigma^2_{i, \eta})\\
    \end{aligned}
\end{gather*}
$$

!!!! note System matrices     When building the system matrices we get rid of the first `lags` observations      in order to build all system matrices respecting the correspondent timestamps

!!! warning Forecasting     The dynamic autorregressive model does not have the [`forecast`](@ref) method implemented yet.      If you wish to perform forecasts with this model please open an issue.

!!! warning Missing values     The dynamic autorregressive model currently does not support missing values (`NaN` observations.)

# Example

```jldoctest
julia> model = DAR(randn(100), 2)
DAR
```
