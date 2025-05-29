```
project(M::Flag, p::OrthogonalPoint, X::OrthogonalTVector)
```

Project vector `X` to tangent space at point `p` from [`Flag`](@ref) manifold `M` $\operatorname{Flag}(n_1, n_2, ..., n_d; N)$, in the orthogonal matrix representation. It works by first projecting `X` to the space of [`SkewHermitianMatrices`](@ref) and then setting diagonal blocks to 0:

$$
X = \begin{bmatrix}
0                     & B_{1,2}               & ⋯ & B_{1,d+1} \\
-B_{1,2}^\mathrm{T}   & 0                     & ⋯ & B_{2,d+1} \\
\vdots                & \vdots                & ⋱ & \vdots    \\
-B_{1,d+1}^\mathrm{T} & -B_{2,d+1}^\mathrm{T} & ⋯ & 0
\end{bmatrix}
$$

where $B_{i,j} ∈ ℝ^{(n_i - n_{i-1}) × (n_j - n_{j-1})}$, for  $1 ≤ i < j ≤ d+1$.
