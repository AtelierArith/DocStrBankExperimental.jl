```
BasicStructural(y::Vector{Fl}, s::Int) where Fl
```

基本的な構造状態空間モデルは、トレンド（レベル + 傾き）と季節成分から構成されています。これは次のように定義されます：

$$
\begin{gather*}
    \begin{aligned}
        y_{t} &=  \mu_{t} + \gamma_{t} + \varepsilon_{t} \quad &\varepsilon_{t} \sim \mathcal{N}(0, \sigma^2_{\varepsilon})\\
        \mu_{t+1} &= \mu_{t} + \nu_{t} + \xi_{t} \quad &\xi_{t} \sim \mathcal{N}(0, \sigma^2_{\xi})\\
        \nu_{t+1} &= \nu_{t} + \zeta_{t} \quad &\zeta_{t} \sim \mathcal{N}(0, \sigma^2_{\zeta})\\
        \gamma_{t+1} &= -\sum_{j=1}^{s-1} \gamma_{t+1-j} + \omega_{t} \quad & \omega_{t} \sim \mathcal{N}(0, \sigma^2_{\omega})\\
    \end{aligned}
\end{gather*}
$$

# 例

```jldoctest
julia> model = BasicStructural(rand(100), 12)
BasicStructural
```

# 参考文献

  * Durbin, James, & Siem Jan Koopman. (2012). "Time Series Analysis by State Space Methods: Second Edition." Oxford University Press.
