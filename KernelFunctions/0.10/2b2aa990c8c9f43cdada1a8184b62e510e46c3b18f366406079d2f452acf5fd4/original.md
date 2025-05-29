```
WienerKernel(; i::Int=0)
WienerKernel{i}()
```

The `i`-times integrated Wiener process kernel function.

# Definition

For inputs $x, x' \in \mathbb{R}^d$, the $i$-times integrated Wiener process kernel with $i \in \{-1, 0, 1, 2, 3\}$ is defined[^SDH] as

$$
k_i(x, x') = \begin{cases}
    \delta(x, x') & \text{if } i=-1,\\
    \min\big(\|x\|_2, \|x'\|_2\big) & \text{if } i=0,\\
    a_{i1}^{-1} \min\big(\|x\|_2, \|x'\|_2\big)^{2i + 1}
    + a_{i2}^{-1} \|x - x'\|_2 r_i\big(\|x\|_2, \|x'\|_2\big) \min\big(\|x\|_2, \|x'\|_2\big)^{i + 1}
    & \text{otherwise},
\end{cases}
$$

where the coefficients $a$ are given by

$$
a = \begin{bmatrix}
3 & 2 \\
20 & 12 \\
252 & 720
\end{bmatrix}
$$

and the functions $r_i$ are defined as

$$
\begin{aligned}
r_1(t, t') &= 1,\\
r_2(t, t') &= t + t' - \frac{\min(t, t')}{2},\\
r_3(t, t') &= 5 \max(t, t')^2 + 2 tt' + 3 \min(t, t')^2.
\end{aligned}
$$

The [`WhiteKernel`](@ref) is recovered for $i = -1$.

[^SDH]: Schober, Duvenaud & Hennig (2014). Probabilistic ODE Solvers with Runge-Kutta Means.
