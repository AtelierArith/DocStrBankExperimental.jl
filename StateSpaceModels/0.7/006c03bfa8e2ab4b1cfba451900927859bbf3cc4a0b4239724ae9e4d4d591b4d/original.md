```
LocalLevelExplanatory(y::Vector{Fl}, X::Matrix{Fl}) where Fl
```

A local level model with explanatory variables is defined by:

$$
\begin{gather*}
    \begin{aligned}
        y_{t} &=  \mu_{t} + X_{1,t} \cdot \beta_{1,t} + \dots + X_{n,t} \cdot \beta_{n,t} + \varepsilon_{t} \quad &\varepsilon_{t} \sim \mathcal{N}(0, \sigma^2_{\varepsilon})\\
        \mu_{t+1} &= \mu_{t} + \xi_{t} &\xi_{t} \sim \mathcal{N}(0, \sigma^2_{\xi})\\
        \beta_{1,t+1} &= \beta_{1,t} &\tau_{1, t} \sim \mathcal{N}(0, \sigma^2_{\tau_{1}})\\
        \dots &= \dots\\
        \beta_{n,t+1} &= \beta_{n,t} &\tau_{n, t} \sim \mathcal{N}(0, \sigma^2_{\tau_{n}})\\\\
    \end{aligned}
\end{gather*}
$$

# Example

```jldoctest
julia> model = LocalLevelExplanatory(rand(100), rand(100, 1))
LocalLevelExplanatory
```
