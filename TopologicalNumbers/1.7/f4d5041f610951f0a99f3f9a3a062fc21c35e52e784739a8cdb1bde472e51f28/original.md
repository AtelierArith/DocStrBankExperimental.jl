Hamiltonian of the two-dimensional square lattice with flux model.

```
 Flux2d(k::T1, p::T2) where {T1<:Union{AbstractVector,Tuple}, T2<:Union{AbstractVector,Tuple}}
```

# Arguments

  * `k::T1`: one-dimensional wavenumber `k`.
  * `p::T2`: parameters defined as below.

# Definition

Hamiltonian of the two-dimensional square lattice with flux model is defined as

$$
H(k)=\begin{pmatrix}
    -2t\cos(k_{2}-2\pi m\frac{1}{n}) & -t                               & 0      & 0  & \cdots                               & e^{-ik_{1}}           \\
    -t                               & -2t\cos(k_{2}-2\pi m\frac{2}{n}) & -t     & 0  & \cdots                               & 0                     \\
    0                                & -t                               & \ddots & -t & \cdots                               & \vdots                \\
    \vdots                           & \vdots                           &        & -t & -2t\cos(k_{2}-2\pi m\frac{(n-1)}{n}) & -t                    \\
    e^{ik_{1}}                       & 0                                & \cdots & 0  & -t                                   & -2t\cos(k_{2}-2\pi m)
\end{pmatrix}
$$

where $t$ is the amplitude of the nearest neighbor hopping in the tight binding model. $n$ and $m$ are the size of the unit cell of the phase produced by the application of the static magnetic field. Nondimensionalize with $t=1$ and $n,m=$`p`.

# Examples

```julia
julia> Flux2d([0, π/3], [4, 1])
4×4 Matrix{ComplexF64}:
 -1.73205+0.0im  -1.0+0.0im      0.0+0.0im  -1.0+0.0im
     -1.0+0.0im   1.0+0.0im     -1.0+0.0im   0.0+0.0im
      0.0+0.0im  -1.0+0.0im  1.73205+0.0im  -1.0+0.0im
     -1.0-0.0im   0.0+0.0im     -1.0+0.0im  -1.0+0.0im
```
