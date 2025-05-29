```
correlation_matrix(psi::MPS,
                   Op1::AbstractString,
                   Op2::AbstractString;
                   kwargs...)

correlation_matrix(psi::MPS,
                   Op1::Matrix{<:Number},
                   Op2::Matrix{<:Number};
                   kwargs...)
```

Given an MPS psi and two strings denoting operators (as recognized by the `op` function), computes the two-point correlation function matrix C[i,j] = <psi| Op1i Op2j |psi> using efficient MPS techniques. Returns the matrix C.

# Optional Keyword Arguments

  * `sites = 1:length(psi)`: compute correlations only  for sites in the given range
  * `ishermitian = false` : if `false`, force independent calculations of the  matrix elements above and below the diagonal, while if `true` assume they are complex conjugates.

For a correlation matrix of size NxN and an MPS of typical bond dimension m, the scaling of this algorithm is N^2*m^3.

# Examples

```julia
N = 30
m = 4

s = siteinds("S=1/2", N)
psi = random_mps(s; linkdims=m)
Czz = correlation_matrix(psi, "Sz", "Sz")
Czz = correlation_matrix(psi, [1/2 0; 0 -1/2], [1/2 0; 0 -1/2]) # same as above

s = siteinds("Electron", N; conserve_qns=true)
psi = random_mps(s, n -> isodd(n) ? "Up" : "Dn"; linkdims=m)
Cuu = correlation_matrix(psi, "Cdagup", "Cup"; sites=2:8)
```
