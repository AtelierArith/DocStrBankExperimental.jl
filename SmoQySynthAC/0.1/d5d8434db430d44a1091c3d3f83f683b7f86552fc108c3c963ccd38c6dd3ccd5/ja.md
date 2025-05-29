```
bose(ϵ::T, β::T) where {T<:AbstractFloat}
```

ボース-アインシュタイン関数

$$
\begin{align*}
n_\beta(\epsilon) & = \overbrace{\left( \frac{1}{e^{\beta\epsilon} - 1}\right)}^{\text{数値的に不安定}} \\
                  & = \underbrace{\frac{1}{2}\left(\coth\left(\frac{\beta\epsilon}{2}\right) - 1 \right)}_{\text{数値的に安定}},
\end{align*}
$$

ここで、$\epsilon$はエネルギー、$\beta$は逆温度です。
