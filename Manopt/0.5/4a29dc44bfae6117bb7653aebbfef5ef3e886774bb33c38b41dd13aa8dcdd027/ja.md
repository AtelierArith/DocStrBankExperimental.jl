```
LinearQuadraticHuber <: SmoothingTechnique
```

指定されたスムージングは、$\max\{0,x\} ≈ \mathcal P(x,u)$ に基づいており、ここで $u$ は次のように定義されます。

$$
\mathcal P(x, u) = \begin{cases}
  0 & \text{ if } x \leq 0,\\
  \frac{x^2}{2u} & \text{ if } 0 \leq x \leq u,\\
  x-\frac{u}{2} & \text{ if } x \geq u.
\end{cases}
$$
