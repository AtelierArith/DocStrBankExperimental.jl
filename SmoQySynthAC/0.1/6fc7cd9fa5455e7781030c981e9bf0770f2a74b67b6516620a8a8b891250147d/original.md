```
fermi(ϵ::T, β::T) where {T<:AbstractFloat}
```

The Fermi-Dirac function

$$
\begin{align*}
f_\beta(\epsilon) & = \overbrace{\left( \frac{1}{e^{\beta\epsilon} + 1}\right)}^{\text{numerically unstable}} \\
                  & = \underbrace{\frac{1}{2}\left( 1 - \tanh\left(\frac{\beta\epsilon}{2}\right) \right)}_{\text{numerically stable}},
\end{align*}
$$

where $\epsilon$ is energy and $\beta$ is inverse temperature.
