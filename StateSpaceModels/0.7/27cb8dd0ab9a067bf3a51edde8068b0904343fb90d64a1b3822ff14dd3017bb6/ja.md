```
BasicStructuralExplanatory(y::Vector{Fl}, s::Int, X::Matrix{Fl}) where Fl
```

これは次のように定義されています：

$$
\begin{gather*}
    \begin{aligned}
        y_{t} &=  \mu_{t} + \gamma_{t} + \beta_{t, i}X_{t, i} \varepsilon_{t} \quad &\varepsilon_{t} \sim \mathcal{N}(0, \sigma^2_{\varepsilon})\\
        \mu_{t+1} &= \mu_{t} + \nu_{t} + \xi_{t} \quad &\xi_{t} \sim \mathcal{N}(0, \sigma^2_{\xi})\\
        \nu_{t+1} &= \nu_{t} + \zeta_{t} \quad &\zeta_{t} \sim \mathcal{N}(0, \sigma^2_{\zeta})\\
        \gamma_{t+1} &= -\sum_{j=1}^{s-1} \gamma_{t+1-j} + \omega_{t} \quad & \omega_{t} \sim \mathcal{N}(0, \sigma^2_{\omega})\\
        \beta_{t+1} &= \beta_{t}
    \end{aligned}
\end{gather*}
$$

# 例

```jldoctest
julia> model = BasicStructuralExplanatory(rand(100), 12, rand(100, 2))
BasicStructuralExplanatory
```

# 参考文献

  * Durbin, James, & Siem Jan Koopman. (2012). "Time Series Analysis by State Space Methods: Second Edition." Oxford University Press.
