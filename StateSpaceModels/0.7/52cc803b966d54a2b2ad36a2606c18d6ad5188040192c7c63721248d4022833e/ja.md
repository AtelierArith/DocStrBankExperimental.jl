```
LinearRegression(X::Matrix{Fl}, y::Vector{Fl}) where Fl
```

線形回帰の状態空間モデルは次のように定義されます：

$$
\begin{gather*}
    \begin{aligned}
        y_{t} &=  X_{1,t} \cdot \beta_{1,t} + \dots + X_{n,t} \cdot \beta_{n,t} + \varepsilon_{t} \quad &\varepsilon_{t} \sim \mathcal{N}(0, \sigma^2_{\varepsilon})\\
        \beta_{1,t+1} &= \beta_{1,t}\\
        \dots &= \dots\\
        \beta_{n,t+1} &= \beta_{n,t}\\
    \end{aligned}
\end{gather*}
$$

# 例

```jldoctest
julia> model = LinearRegression(rand(100, 2), rand(100))
LinearRegression
```
