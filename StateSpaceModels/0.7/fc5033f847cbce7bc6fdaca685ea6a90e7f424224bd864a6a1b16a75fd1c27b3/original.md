```
LocalLevelCycle(y::Vector{Fl}) where Fl
```

The local level model with a cycle component is defined by:

$$
\begin{gather*}
    \begin{aligned}
        y_{t} &=  \mu_{t} + c_{t} + \varepsilon_{t} \quad &\varepsilon_{t} \sim \mathcal{N}(0, \sigma^2_{\varepsilon})\\
        \mu_{t+1} &= \mu_{t} + \eta_{t} \quad &\eta_{t} \sim \mathcal{N}(0, \sigma^2_{\eta})\\
        c_{t+1} &= c_{t} \cos(\lambda_c) + c_{t}^{*} \sin(\lambda_c)\ \quad & \tilde\omega_{t} \sim \mathcal{N}(0, \sigma^2_{\tilde\omega})\\
        c_{t+1}^{*} &= -c_{t} \sin(\lambda_c) + c_{t}^{*} \sin(\lambda_c) \quad &\tilde\omega^*_{t} \sim \mathcal{N}(0, \sigma^2_{\tilde\omega})\\
    \end{aligned}
\end{gather*}
$$

# Example

```jldoctest
julia> model = LocalLevelCycle(rand(100))
LocalLevelCycle
```

See more on TODO RJ_TEMPERATURE

# References

  * Durbin, James, & Siem Jan Koopman. (2012). "Time Series Analysis by State Space Methods: Second Edition." Oxford University Press. pp. 48
