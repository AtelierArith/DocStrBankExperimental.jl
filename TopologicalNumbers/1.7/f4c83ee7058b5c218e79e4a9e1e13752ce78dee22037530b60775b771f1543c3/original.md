Hamiltonian of the Kitaev chain model.

```
 KitaevChain(k::T1, p::T2) where {T1<:Real, T2<:Union{AbstractVector,Tuple}}
```

# Arguments

  * `k::T1`: one-dimensional wavenumber `k`.
  * `p::T2`: parameters defined as below.

# Definition

Hamiltonian of the Kitaev chain model is defined as

$$
H(k)=\begin{pmatrix}
    -\mu-2t\cos(k)   & 2i\Delta\sin(k) \\
    -2i\Delta\sin(k) & \mu+2t\cos(k)
\end{pmatrix}
$$

where $t$ is the amplitude of the nearest neighbor hopping in the tight binding model. $\Delta$ is the pairing with the nearest neighbor site, $\mu$ is the chemical potential. Nondimensionalize with $t=1$ and $\mu,\Delta=$`p`.

# Examples

```julia
julia> SSH(π/3, 0.5)
2×2 Matrix{ComplexF64}:
 -0.5+0.0im       0.0+0.866025im
  0.0-0.866025im  0.5+0.0im
```
