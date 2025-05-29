```
inv_IpUV!(G::AbstractMatrix{T}, U::LDR{T,E}, V::LDR{T,E}, ws::LDRWorkspace{T,E})::Tuple{E,T} where {T,E}
```

Calculate the numerically stable inverse $G := [I + UV]^{-1},$ where $G$ is a matrix and $U$ and $V$ are represented by [`LDR`](@ref) factorizations. This method also returns $\log( \vert \det G\vert )$ and $\textrm{sign}(\det G).$

# Algorithm

The numerically stable inverse $G := [I + UV]^{-1}$ is calculated using the procedure

$$
\begin{align*}
G:= & [I+UV]^{-1}\\
= & [I+L_{u}D_{u}R_{u}L_{v}D_{v}R_{v}]^{-1}\\
= & [I+L_{u}D_{u,\max}D_{u,\min}R_{u}L_{v}D_{v,\min}D_{v,\max}R_{v}]^{-1}\\
= & [L_{u}D_{u,\max}(D_{u,\max}^{-1}L_{u}^{\dagger}R_{v}^{-1}D_{v,\max}^{-1}+D_{u,\min}R_{u}L_{v}D_{v,\min})D_{v,\max}R_{v}]^{-1}\\
= & R_{v}^{-1}D_{v,\max}^{-1}[\overset{M}{\overbrace{D_{u,\max}^{-1}L_{u}^{\dagger}R_{v}^{-1}D_{v,\max}^{-1}+D_{u,\min}R_{u}L_{v}D_{v,\min}}}]^{-1}D_{u,\max}^{-1}L_{u}^{\dagger}\\
= & R_{v}^{-1}D_{v,\max}^{-1}M^{-1}D_{u,\max}^{-1}L_{u}^{\dagger}
\end{align*}
$$

Intermediate matrix inversions and relevant determinant calculations are performed via LU factorizations with partial pivoting.
