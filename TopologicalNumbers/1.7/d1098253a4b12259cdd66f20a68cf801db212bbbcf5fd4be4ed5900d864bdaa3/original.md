Hamiltonian of the Thouless pumping model.

```
 ThoulessPump(k::T1, p::T2) where {T1<:Union{AbstractVector,Tuple}, T2<:Union{AbstractVector,Tuple}}
```

# Arguments

  * `k::T1`: when one-dimensional wavenumber `k₁` and time `t`, `k=[k₁, t]`.
  * `p::T2`: parameters defined as below.

# Definition

Hamiltonian of the Kane–Mele model is defined as

$$
H(k)=\begin{pmatrix}
    h_{3}(\bm{k})                 & h_{5}(\bm{k})-ih_{4}(\bm{k}) & 0                            & -h_{5}(\bm{k})-ih_{1}(\bm{k}) \\
    h_{5}(\bm{k})+ih_{4}(\bm{k})  & -h_{3}(\bm{k})               & h_{5}(\bm{k})-ih_{1}(\bm{k}) & 0                             \\
    0                             & h_{5}(\bm{k})+ih_{1}(\bm{k}) & -h_{3}(\bm{k})               & h_{5}(\bm{k})-ih_{4}(\bm{k})  \\
    -h_{5}(\bm{k})+ih_{1}(\bm{k}) & 0                            & h_{5}(\bm{k})+ih_{4}(\bm{k}) & h_{3}(\bm{k})
\end{pmatrix}
$$

$$
\begin{align*}
     h_{1}(\bm{k})=&-\Delta\sin(k_{1}) \\
     h_{2}(\bm{k})=&-\Delta(1-\cos(k_{1})) \\
     h_{3}(\bm{k})=&m_{0}\sin(t) \\
     h_{4}(\bm{k})=&-t_{0}(1+\cos(t))\sin(k_{1}) \\
     h_{5}(\bm{k})=&-t_{0}(1-\cos(t))-t_{0}(1+\cos(t)))\cos(k_{1})
\end{align*}
$$

where $t_{0}$ is the amplitude of the nearest neighbor hopping in the tight binding model. $m_{0}$ is the magnitude of the alternating magnetic field. $\Delta$ is the magnitude of spin flip interaction. Nondimensionalize with $t_{0}=1$ and $m_{0},\Delta=$`p`.

# Examples

```julia
julia> ThoulessPump([0, π/3], (-1.0, 0.5))
4×4 Matrix{ComplexF64}:
 -0.866025-0.0im      -2.0+0.0im      -0.0-0.0im        0.0+0.0im
      -2.0-0.0im  0.866025-0.0im      -0.0+0.0im       -0.0-0.0im
      -0.0-0.0im      -0.0-0.0im  0.866025-0.0im       -2.0+0.0im
       0.0-0.0im      -0.0-0.0im      -2.0-0.0im  -0.866025-0.0im
```
