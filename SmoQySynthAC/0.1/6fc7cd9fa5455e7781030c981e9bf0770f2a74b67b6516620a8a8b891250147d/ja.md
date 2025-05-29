```
fermi(ϵ::T, β::T) where {T<:AbstractFloat}
```

フェルミ-ディラック関数

$$
\begin{align*}
f_\beta(\epsilon) & = \overbrace{\left( \frac{1}{e^{\beta\epsilon} + 1}\right)}^{\text{数値的に不安定}} \\
                  & = \underbrace{\frac{1}{2}\left( 1 - \tanh\left(\frac{\beta\epsilon}{2}\right) \right)}_{\text{数値的に安定}},
\end{align*}
$$

ここで、$\epsilon$はエネルギー、$\beta$は逆温度です。
