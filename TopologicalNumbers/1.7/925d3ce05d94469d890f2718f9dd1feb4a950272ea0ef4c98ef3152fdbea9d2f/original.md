Hamiltonian of the Bernevig–Hughes–Zhang (BHZ) model.

```
 BHZ(k::T1, p::T2) where {T1<:Union{AbstractVector,Tuple}, T2<:Union{AbstractVector,Tuple}}
```

# Arguments

  * `k::T1`: two-dimensional wavenumber `k`.
  * `p::T2`: parameters defined as below.

# Definition

Hamiltonian of the BHZ model is defined as

$$
H(k)=\begin{pmatrix}
    h_{0}(\bm{k})+h_{3}(\bm{k})  & 0                            & h_{5}(\bm{k})-ih_{4}(\bm{k}) & 0                            \\
    0                            & h_{0}(\bm{k})-h_{3}(\bm{k})  & 0                            & h_{5}(\bm{k})-ih_{4}(\bm{k}) \\
    h_{5}(\bm{k})+ih_{4}(\bm{k}) & 0                            & h_{0}(\bm{k})-h_{3}(\bm{k})  & 0                            \\
    0                            & h_{5}(\bm{k})+ih_{4}(\bm{k}) & 0                            & h_{0}(\bm{k})+h_{3}(\bm{k})
\end{pmatrix}
$$

$$
\begin{align*}
     h_{0}(\bm{k})=&-(t_{ss}-t_{pp})(\cos(k_{1})+\cos(k_{2}))+\frac{(\epsilon_{s}+\epsilon_{p})}{2} \\
     h_{3}(\bm{k})=&2t_{sp}\sin(k_{2}) \\
     h_{4}(\bm{k})=&2t_{sp}\sin(k_{1}) \\
     h_{5}(\bm{k})=&-(t_{ss}+t_{pp})(\cos(k_{1})+\cos(k_{2}))+\frac{(\epsilon_{s}-\epsilon_{p})}{2}
\end{align*}
$$

where $t_{sp}$ is the amplitude of the mixed hopping between s- and p-orbitals in the tight binding model. $t_{ss}$ is the hopping between s-orbitals, $t_{pp}$ is the hopping between p-orbitals, and $t_{1}=t_{s}-t_{p}$, $t_{2}=t_{s}+t_{p}$. $\epsilon_{s}$ and $\epsilon_{p}$ are the site potential terms for the s- and p-orbitals, $\epsilon_{1}\epsilon_{s}s+\epsilon_{p}$, $\epsilon_{2}=\epsilon_{s}-\epsilon_{p}. Nondimensionalize with $t_{sp}=t_{1}=\epsilon_{1}=1$ and $\epsilon_{2},t_{2}=$`p`.

# Examples

```julia
julia> BHZ([0, π/3], [0.5, 0.5])
4×4 Matrix{ComplexF64}:
 0.732051+0.0im       0.0+0.0im      -0.5+0.0im       0.0+0.0im
      0.0+0.0im  -2.73205+0.0im       0.0+0.0im      -0.5+0.0im
     -0.5+0.0im       0.0+0.0im  -2.73205+0.0im       0.0+0.0im
      0.0+0.0im      -0.5+0.0im       0.0+0.0im  0.732051+0.0im
```
