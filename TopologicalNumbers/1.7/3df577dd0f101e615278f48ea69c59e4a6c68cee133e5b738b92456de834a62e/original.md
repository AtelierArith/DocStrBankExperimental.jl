Hamiltonian of the Su-Schrieffer-Heeger model.

```
 SSH(k::T1, p::T2) where {T1<:Real,T2<:Real}
```

# Arguments

  * `k::T1`: one-dimensional wavenumber `k`.
  * `p::T2`: parameter defined as below.

# Definition

Hamiltonian of the Su-Schrieffer-Heeger model is defined as

$$
H(k)=\begin{pmatrix}
    0                 & t_{1}+t_{2}e^{-ik} \\
    t_{1}+t_{2}e^{ik} & 0
\end{pmatrix}
$$

where $t_{1}$ and $t_{2}$ are the amplitudes of the nearest neighbor hopping in the tight binding model. Nondimensionalize with $t_{1}=1$ and $t_{2}=$`p`.

# Examples

```julia
julia> SSH(π/3, 0.5)
2×2 Matrix{ComplexF64}:
  0.0+0.0im       1.25-0.433013im
 1.25+0.433013im   0.0+0.0im
```
