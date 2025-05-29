```
LinearQuadraticHuber <: SmoothingTechnique
```

Specify a smoothing based on $\max\{0,x\} ≈ \mathcal P(x,u)$ for some $u$, where

$$
\mathcal P(x, u) = \begin{cases}
  0 & \text{ if } x \leq 0,\\
  \frac{x^2}{2u} & \text{ if } 0 \leq x \leq u,\\
  x-\frac{u}{2} & \text{ if } x \geq u.
\end{cases}
$$
