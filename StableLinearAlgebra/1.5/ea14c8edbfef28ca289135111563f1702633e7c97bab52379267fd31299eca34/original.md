```
inv_IpA!(G::AbstractMatrix{T}, A::LDR{T,E}, ws::LDRWorkspace{T,E})::Tuple{E,T} where {T,E}
```

Calculate the numerically stable inverse $G := [I + A]^{-1},$ where $G$ is a matrix, and $A$ is represented by a [`LDR`](@ref) factorization. This method also returns $\log( \vert \det G\vert )$ and $\textrm{sign}(\det G).$

# Algorithm

The numerically stable inverse $G := [I + A]^{-1}$ is calculated using the procedure

$$
\begin{align*}
G:= & [I+A]^{-1}\\
= & [I+L_{a}D_{a}R_{a}]^{-1}\\
= & [I+L_{a}D_{a,\min}D_{a,\max}R_{a}]^{-1}\\
= & [(R_{a}^{-1}D_{a,\max}^{-1}+L_{a}D_{a,\min})D_{a,\max}R_{a}]^{-1}\\
= & R_{a}^{-1}D_{a,\max}^{-1}[\overset{M}{\overbrace{R_{a}^{-1}D_{a,\max}^{-1}+L_{a}D_{a,\min}}}]^{-1}\\
= & R_{a}^{-1}D_{a,\max}^{-1}M^{-1},
\end{align*}
$$

where $D_{a,\min} = \min(D_a, 1)$ and $D_{a,\max} = \max(D_a, 1).$ Intermediate matrix inversions and relevant determinant calculations are performed via LU factorizations with partial pivoting.
