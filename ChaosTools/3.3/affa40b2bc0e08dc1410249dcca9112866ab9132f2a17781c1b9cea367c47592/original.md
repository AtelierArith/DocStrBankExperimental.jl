```
broomhead_king(s::AbstractVector, d::Int) -> U, S, Vtr
```

Return the Broomhead-King coordinates of a timeseries `s` by performing `svd` on high-dimensional delay embedding if `s` with dimension `d` with minimum delay.

## Description

Broomhead and King coordinates is an approach proposed in [^Broomhead1987] that applies the Karhunen–Loève theorem to delay coordinates embedding with smallest possible delay.

The function performs singular value decomposition on the `d`-dimensional matrix $X$ of $s$,

$$
X = \frac{1}{\sqrt{N}}\left(
\begin{array}{cccc}
x_1 & x_2 & \ldots & x_d \\
x_2 & x_3 & \ldots & x_{d+1}\\
\vdots & \vdots & \vdots & \vdots \\
x_{N-d+1} & x_{N-d+2} &\ldots & x_N
\end{array}
\right) = U\cdot S \cdot V^{tr}.
$$

where $x := s - \bar{s}$. The columns of $U$ can then be used as a new coordinate system, and by considering the values of the singular values $S$ you can decide how many columns of $U$ are "important".

[^Broomhead1987]: Broomhead, Jones, King, J. Phys. A **20**, 9, pp L563 (1987)
