Hamiltonian of the Kane–Mele model.

```
 KaneMele(k::T1, p::T2) where {T1<:Union{AbstractVector,Tuple}, T2<:Real}
```

# Arguments

  * `k::T1`: two-dimensional wavenumber `k`.
  * `p::T2`: parameter defined as below.

# Definition

Hamiltonian of the Kane–Mele model is defined as

$$
H(k)=\begin{pmatrix}
    h_{3}(\bm{k})                & 0                            & h_{5}(\bm{k})-ih_{4}(\bm{k}) & 0                            \\
    0                            & -h_{3}(\bm{k})               & 0                            & h_{5}(\bm{k})-ih_{4}(\bm{k}) \\
    h_{5}(\bm{k})+ih_{4}(\bm{k}) & 0                            & -h_{3}(\bm{k})               & 0                            \\
    0                            & h_{5}(\bm{k})+ih_{4}(\bm{k}) & 0                            & h_{3}(\bm{k})
\end{pmatrix}
$$

$$
\begin{align*}
     h_{3}(\bm{k})=&2\lambda_{\mathrm{SO}}(\sin(k_{1})-\sin(k_{2})-\sin(k_{1}-k_{2})) \\
     h_{4}(\bm{k})=&-t(\sin(k_{1})+\sin(k_{2})) \\
     h_{5}(\bm{k})=&-t(\cos(k_{1})+\cos(k_{2})+1)
\end{align*}
$$

where $t$ is the amplitude of the nearest neighbor hopping in the tight binding model. $\lambda_{\mathrm{SO}}$ is the magnitude of spin-orbit interaction. Nondimensionalize with $t=1$ and $\lambda_{\mathrm{SO}}=$`p`.

# Examples

```julia
julia> KaneMele([0, π/3], 0.5)
4×4 Matrix{ComplexF64}:
  0.0+0.0im        0.0+0.0im       -2.5+0.866025im   0.0+0.0im
  0.0+0.0im        0.0+0.0im        0.0+0.0im       -2.5+0.866025im
 -2.5-0.866025im   0.0+0.0im        0.0+0.0im        0.0+0.0im
  0.0+0.0im       -2.5-0.866025im   0.0+0.0im        0.0+0.0im
```
