```
LocalLevel(y::Vector{Fl}) where Fl
```

ローカルレベルモデルは次のように定義されます：

$$
\begin{gather*}
    \begin{aligned}
        y_{t} &=  \mu_{t} + \varepsilon_{t} \quad \varepsilon_{t} \sim \mathcal{N}(0, \sigma^2_{\varepsilon})\\
        \mu_{t+1} &= \mu_{t} + \eta_{t} \quad \eta_{t} \sim \mathcal{N}(0, \sigma^2_{\eta})\\
    \end{aligned}
\end{gather*}
$$

# 例

```jldoctest
julia> model = LocalLevel(rand(100))
LocalLevel
```

[Nile river annual flow](@ref)の詳細を参照してください。

# 参考文献

  * Durbin, James, & Siem Jan Koopman. (2012). "Time Series Analysis by State Space Methods: Second Edition." Oxford University Press. pp. 9
