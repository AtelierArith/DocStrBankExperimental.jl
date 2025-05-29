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

線形単変量時間変化状態空間モデルのシステム行列 $y, Z, d, T, c, R, H, Q$ の定義。

$$
\begin{gather*}
    \begin{aligned}
        y_{t} &=  Z_{t}\alpha_{t} + d_{t} + \varepsilon_{t} \quad &\varepsilon_{t} \sim \mathcal{N}(0, H_{t})\\
        \alpha_{t+1} &= T_{t}\alpha_{t} + c_{t} + R_{t}\eta_{t} \quad &\eta_{t} \sim \mathcal{N}(0, Q_{t})\\
    \end{aligned}
\end{gather*}
$$

ここで：

  * $$
    y_{t}
    $$

    はスカラー
  * $$
    Z_{t}
    $$

    は $m \times 1$ ベクトル
  * $$
    d_{t}
    $$

    はスカラー
  * $$
    T_{t}
    $$

    は $m \times m$ 行列
  * $$
    c_{t}
    $$

    は $m \times 1$ ベクトル
  * $$
    R_{t}
    $$

    は $m \times r$ 行列
  * $$
    H_{t}
    $$

    はスカラー
  * $$
    Q_{t}
    $$

    は $r \times r$ 行列
