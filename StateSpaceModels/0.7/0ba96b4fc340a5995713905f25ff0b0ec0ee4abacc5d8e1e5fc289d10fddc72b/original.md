```
LinearUnivariateTimeVariant{Fl}(
    y::Vector{Fl},
    Z::Vector{Vector{Fl}},
    T::Vector{Matrix{Fl}},
    R::Vector{Matrix{Fl}},
    d::Vector{Fl},
    c::Vector{Vector{Fl}},
    H::Vector{Fl},
    Q::Vector{Matrix{Fl}},
) where Fl <: AbstractFloat
```

Definition of the system matrices $y, Z, d, T, c, R, H, Q$ for linear univariate time variant state space models.

$$
\begin{gather*}
    \begin{aligned}
        y_{t} &=  Z_{t}\alpha_{t} + d_{t} + \varepsilon_{t} \quad &\varepsilon_{t} \sim \mathcal{N}(0, H_{t})\\
        \alpha_{t+1} &= T_{t}\alpha_{t} + c_{t} + R_{t}\eta_{t} \quad &\eta_{t} \sim \mathcal{N}(0, Q_{t})\\
    \end{aligned}
\end{gather*}
$$

where:

  * $y_{t}$ is a scalar
  * $Z_{t}$ is a $m \times 1$ vector
  * $d_{t}$ is a scalar
  * $T_{t}$ is a $m \times m$ matrix
  * $c_{t}$ is a $m \times 1$ vector
  * $R_{t}$ is a $m \times r$ matrix
  * $H_{t}$ is a scalar
  * $Q_{t}$ is a $r \times r$ matrix
