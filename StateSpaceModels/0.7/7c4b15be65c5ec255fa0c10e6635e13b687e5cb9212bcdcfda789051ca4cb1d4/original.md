```
LinearUnivariateTimeInvariant{Fl}(
    y::Vector{Fl},
    Z::Vector{Fl},
    T::Matrix{Fl},
    R::Matrix{Fl},
    d::Fl,
    c::Vector{Fl},
    H::Fl,
    Q::Matrix{Fl},
) where Fl <: AbstractFloat
```

Definition of the system matrices $y, Z, d, T, c, R, H, Q$ for linear univariate time invariant state space models.

$$
\begin{gather*}
    \begin{aligned}
        y_{t} &=  Z\alpha_{t} + d + \varepsilon_{t} \quad &\varepsilon_{t} \sim \mathcal{N}(0, H)\\
        \alpha_{t+1} &= T\alpha_{t} + c + R\eta_{t} \quad &\eta_{t} \sim \mathcal{N}(0, Q)\\
    \end{aligned}
\end{gather*}
$$

where:

  * $y_{t}$ is a scalar
  * $Z$ is a $m \times 1$ vector
  * $d$ is a scalar
  * $T$ is a $m \times m$ matrix
  * $c$ is a $m \times 1$ vector
  * $R$ is a $m \times r$ matrix
  * $H$ is a scalar
  * $Q$ is a $r \times r$ matrix
