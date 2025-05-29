```
LocalLevel(y::Vector{Fl}) where Fl
```

The local level model is defined by:

$$
\begin{gather*}
    \begin{aligned}
        y_{t} &=  \mu_{t} + \varepsilon_{t} \quad \varepsilon_{t} \sim \mathcal{N}(0, \sigma^2_{\varepsilon})\\
        \mu_{t+1} &= \mu_{t} + \eta_{t} \quad \eta_{t} \sim \mathcal{N}(0, \sigma^2_{\eta})\\
    \end{aligned}
\end{gather*}
$$

# Example

```jldoctest
julia> model = LocalLevel(rand(100))
LocalLevel
```

See more on [Nile river annual flow](@ref)

# References

  * Durbin, James, & Siem Jan Koopman. (2012). "Time Series Analysis by State Space Methods: Second Edition." Oxford University Press. pp. 9
