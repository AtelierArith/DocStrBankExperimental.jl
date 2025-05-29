```
m, ω = ncfmargin(P, K)
```

Normalized coprime factor margin, defined has the *inverse* of

$$
\begin{Vmatrix}
\begin{bmatrix}
I \\ K
\end{bmatrix} (I + PK)^{-1} \begin{bmatrix}
I & P
\end{bmatrix}
\end{Vmatrix}_\infty
$$

A margin ≥ 0.25-0.3 is a reasonable for robustness. 

If controller `K` stabilizes `P` with margin `m`, then `K` will also stabilize `P̃` if `nugap(P, P̃) < m`.

See also [`extended_gangoffour`](@ref), [`diskmargin`](@ref), [`controller_reduction_plot`](@ref).

# Extended help

  * Robustness with respect to coprime factor uncertainty does not necessarily imply robustness with respect to input uncertainty. Skogestad p. 96 remark 4
