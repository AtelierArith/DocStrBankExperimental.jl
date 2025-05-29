```
Quadratic{D, T<:Real, L}
Quadratic(a,b,c)
```

A struct that represents quadratic polynomial on $\mathbb{R}^D$.

$$
\begin{aligned}
q(p) &= \frac{1}{2}p^{\intercal} A p + b^{\intercal} p + c \\
A &= \begin{pmatrix}
a_1     & a_2      & \cdots & a_D \\
a_2     & a_{D+1}  & \cdots & a_{2D-1} \\
\vdots & \vdots  & \ddots & \vdots \\
a_D     & a_{2D-1} & \cdots & a_{L}
\end{pmatrix}
\end{aligned}
$$

# Examples

```jldoctest
julia> q = Quadratic{2}([2.0, 1.0, 3.0], [-1.2, -2.3], 4.5)
Quadratic{2, Float64, 3}([2.0, 1.0, 3.0], [-1.2, -2.3], 4.5)

julia> q([1,2])
7.7
```
