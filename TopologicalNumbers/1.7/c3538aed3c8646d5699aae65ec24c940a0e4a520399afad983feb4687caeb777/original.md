Hamiltonian of the Kitaev honeycomb model.

```
 KitaevHoneycomb(k::T1, p::T2) where {T1<:Union{AbstractVector,Tuple}, T2<:Real}
```

# Arguments

  * `k::T1`: two-dimensional wavenumber `k`.
  * `p::T2`: parameter defined as below.

# Definition

Hamiltonian of the Kitaev honeycomb model is defined as

$$
H(\bm{k})=\begin{pmatrix}
    h_{3}(\bm{k})                & h_{1}(\bm{k})-ih_{2}(\bm{k}) \\
    h_{1}(\bm{k})+ih_{2}(\bm{k}) & -h_{3}(\bm{k})
\end{pmatrix}
$$

$$
\begin{align*}
     h_{1}(\bm{k})=&-K_{2}(\sin(k_{2})-\sin(k_{1})+\sin(k_{1}-k_{2})) \\
     h_{2}(\bm{k})=&-K_{1}(\sin(k_{1})+\sin(k_{2})) \\
     h_{3}(\bm{k})=&K_{1}(\cos(k_{1})+\cos(k_{2})+1)
\end{align*}
$$

where $K_{1}$ is the magnitude of Kitaev interaction. $K_{2}$ is the magnitude of spin triples term due to magnetic field. Nondimensionalize with $K_{1}=1$ and $K_{2}=$`p`.

# Examples

```julia
julia> KitaevHoneycomb([0, π/3], 0.5)
2×2 Matrix{ComplexF64}:
 2.5-0.0im        0.0+0.866025im
 0.0-0.866025im  -2.5-0.0im
```
