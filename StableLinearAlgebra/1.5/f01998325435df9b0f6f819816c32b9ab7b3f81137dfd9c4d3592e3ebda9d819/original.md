```
inv_invUpV!(G::AbstractMatrix{T}, U::LDR{T,E}, V::LDR{T,E}, ws::LDRWorkspace{T,E})::Tuple{E,T} where {T,E}
```

Calculate the numerically stable inverse $G := [U^{-1}+V]^{-1},$ where $G$ is a matrix and $U$ and $V$ are represented by [`LDR`](@ref) factorizations. This method also returns $\log( \vert \det G\vert )$ and $\textrm{sign}(\det G).$

# Algorithm

The numerically stable inverse $G := [U^{-1}+V]^{-1}$ is calculated using the procedure

$$
\begin{align*}
G:= & [U^{-1}+V]^{-1}\\
= & [\overset{D_{u,\max}D_{u,\min}}{(L_{u}\overbrace{D_{u}}R_{u})^{-1}}+\overset{D_{v,\min}D_{v,\max}}{L_{v}\overbrace{D_{v}}R_{v}}]^{-1}\\
= & [(L_{u}D_{u,\max}D_{u,\min}R_{u})^{-1}+L_{v}D_{v,\min}D_{v,\max}R_{v}]^{-1}\\
= & [R_{u}^{-1}D_{u,\min}^{-1}D_{u,\max}^{-1}L_{u}^{\dagger}+L_{v}D_{v,\min}D_{v,\max}R_{v}]^{-1}\\
= & [R_{u}^{-1}D_{u,\min}^{-1}(D_{u,\max}^{-1}L_{u}^{\dagger}R_{v}^{-1}D_{v,\max}^{-1}+D_{u,\min}R_{u}L_{v}D_{v,\min})D_{v,\max}R_{v}]^{-1}\\
= & R_{v}^{-1}D_{v,\max}^{-1}[\overset{M}{\overbrace{D_{u,\max}^{-1}L_{u}^{\dagger}R_{v}^{-1}D_{v,\max}^{-1}+D_{u,\min}R_{u}L_{v}D_{v,\min}}}]^{-1}D_{u,\min}R_{u}\\
= & R_{v}^{-1}D_{v,\max}^{-1}M^{-1}D_{u,\min}R_{u}
\end{align*}
$$

where

$$
\begin{align*}
D_{u,\min} = & \min(D_u,1)\\
D_{u,\max} = & \max(D_u,1)\\
D_{v,\min} = & \min(D_v,1)\\
D_{v,\max} = & \max(D_v,1),
\end{align*}
$$

and all intermediate matrix inversions and determinant calculations are performed via LU factorizations with partial pivoting.
