```
bose(ϵ::T, β::T) where {T<:AbstractFloat}
```

The Bose-Einstein function

$$
\begin{align*}
n_\beta(\epsilon) & = \overbrace{\left( \frac{1}{e^{\beta\epsilon} - 1}\right)}^{\text{numerically unstable}} \\
                  & = \underbrace{\frac{1}{2}\left(\coth\left(\frac{\beta\epsilon}{2}\right) - 1 \right)}_{\text{numerically stable}},
\end{align*}
$$

where $\epsilon$ is energy and $\beta$ is inverse temperature.
