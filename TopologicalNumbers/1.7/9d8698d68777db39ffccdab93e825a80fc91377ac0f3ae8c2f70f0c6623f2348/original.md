Hamiltonian of the Haldane model.

```
 Haldane(k::T1, p::T2) where {T1<:Union{AbstractVector,Tuple}, T2<:Union{AbstractVector,Tuple}}
```

# Arguments

  * `k::T1`: two-dimensional wavenumber `k`.
  * `p::T2`: parameters defined as below.

# Definition

Hamiltonian of the Haldane model is defined as

$$
H(\bm{k})=\begin{pmatrix}
    h_{0}(\bm{k})+h_{3}(\bm{k})  & h_{1}(\bm{k})-ih_{2}(\bm{k}) \\
    h_{1}(\bm{k})+ih_{2}(\bm{k}) & h_{0}(\bm{k})-h_{3}(\bm{k})
\end{pmatrix}
$$

$$
\begin{align*}
     h_{0}(\bm{k})=&2t_{2}\cos(\phi)(\sin(k_{1})+\sin(k_{2})+\sin(k_{1}+k_{2})) \\
     h_{1}(\bm{k})=&-t_{1}(1+\cos(k_{1})+\cos(k_{2})) \\
     h_{2}(\bm{k})=&-t_{1}(-\sin(k_{1})+\sin(k_{2})) \\
     h_{3}(\bm{k})=&m+2t_{2}\sin(\phi)(\sin(k_{1})+\sin(k_{2})-\sin(k_{1}+k_{2}))
\end{align*}
$$

where $t_{1}$ and $t_{2}$ are the amplitudes of the nearest and the next nearest neighbor hopping in the tight binding model. $\phi$ is the phase produced by the application of the static magnetic field. Nondimensionalize with $t_{1}=1$ and $t_{2},\phi,m=$`p`.

# Examples

```julia
julia> Haldane([0, π/3], [0.5, π/2, 0.3])
2×2 Matrix{ComplexF64}:
  0.3-0.0im       -2.5+0.866025im
 -2.5-0.866025im  -0.3-0.0im
```
