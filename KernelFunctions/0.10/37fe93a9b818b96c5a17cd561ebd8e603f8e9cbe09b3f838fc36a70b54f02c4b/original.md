```
PiecewisePolynomialKernel(; dim::Int, degree::Int=0, metric=Euclidean())
PiecewisePolynomialKernel{degree}(; dim::Int, metric=Euclidean())
```

Piecewise polynomial kernel of degree `degree` for inputs of dimension `dim` with support in the unit ball with respect to the `metric`.

# Definition

For inputs $x, x'$ of dimension $m$ and metric $d(\cdot, \cdot)$, the piecewise polynomial kernel of degree $v \in \{0,1,2,3\}$ is defined as

$$
k(x, x'; v) = \max(1 - d(x, x'), 0)^{\alpha(v,m)} f_{v,m}(d(x, x')),
$$

where $\alpha(v, m) = \lfloor \frac{m}{2}\rfloor + 2v + 1$ and $f_{v,m}$ are polynomials of degree $v$ given by

$$
\begin{aligned}
f_{0,m}(r) &= 1, \\
f_{1,m}(r) &= 1 + (j + 1) r, \\
f_{2,m}(r) &= 1 + (j + 2) r + \big((j^2 + 4j + 3) / 3\big) r^2, \\
f_{3,m}(r) &= 1 + (j + 3) r + \big((6 j^2 + 36j + 45) / 15\big) r^2 + \big((j^3 + 9 j^2 + 23j + 15) / 15\big) r^3,
\end{aligned}
$$

where $j = \lfloor \frac{m}{2}\rfloor + v + 1$. By default, $d$ is the Euclidean metric $d(x, x') = \|x - x'\|_2$.

The kernel is $2v$ times continuously differentiable and the corresponding Gaussian process is hence $v$ times mean-square differentiable.
