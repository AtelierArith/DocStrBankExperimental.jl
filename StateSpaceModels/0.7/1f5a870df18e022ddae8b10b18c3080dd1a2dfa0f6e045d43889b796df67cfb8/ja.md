```
LocalLinearTrend(y::Vector{Fl}) where Fl
```

線形トレンドモデルは次のように定義されます：

$$
\begin{gather*}
    \begin{aligned}
        y_{t} &=  \mu_{t} + \gamma_{t} + \varepsilon_{t} \quad &\varepsilon_{t} \sim \mathcal{N}(0, \sigma^2_{\varepsilon})\\
        \mu_{t+1} &= \mu_{t} + \nu_{t} + \xi_{t} \quad &\xi_{t} \sim \mathcal{N}(0, \sigma^2_{\xi})\\
        \nu_{t+1} &= \nu_{t} + \zeta_{t} \quad &\zeta_{t} \sim \mathcal{N}(0, \sigma^2_{\zeta})\\
    \end{aligned}
\end{gather*}
$$

# 例

```jldoctest
julia> model = LocalLinearTrend(rand(100))
LocalLinearTrend
```

[フィンランドの交通事故による死亡者数](@ref)についての詳細

# 参考文献

  * Durbin, James, & Siem Jan Koopman. (2012). "Time Series Analysis by State Space Methods:  Second Edition." Oxford University Press. pp. 44
