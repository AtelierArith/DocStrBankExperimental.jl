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

線形単変量時間不変状態空間モデルのシステム行列 $y, Z, d, T, c, R, H, Q$ の定義。

$$
\begin{gather*}
    \begin{aligned}
        y_{t} &=  Z\alpha_{t} + d + \varepsilon_{t} \quad &\varepsilon_{t} \sim \mathcal{N}(0, H)\\
        \alpha_{t+1} &= T\alpha_{t} + c + R\eta_{t} \quad &\eta_{t} \sim \mathcal{N}(0, Q)\\
    \end{aligned}
\end{gather*}
$$

ここで：

  * $$
    y_{t}
    $$

    はスカラー
  * $$
    Z
    $$

    は $m \times 1$ ベクトル
  * $$
    d
    $$

    はスカラー
  * $$
    T
    $$

    は $m \times m$ 行列
  * $$
    c
    $$

    は $m \times 1$ ベクトル
  * $$
    R
    $$

    は $m \times r$ 行列
  * $$
    H
    $$

    はスカラー
  * $$
    Q
    $$

    は $r \times r$ 行列
