```
FermionGreensCalculator{T<:Continuous, E<:AbstractFloat}
```

A type to facilitate calculating the single-particle fermion Green's function matrix.

# Fields

  * `forward::Bool`: If `true` then iterate over imaginary time slices from $l=1$ to $l=L_\tau$, if `false` then iterate over imaginary time slices from $l=L_\tau$ to $l=1$.
  * `l::Int`: The current imaginary time slice $\tau = l \cdot \Delta\tau$.
  * `n_stab::Int`: Frequency with which numerical stabilization is performed, i.e. every $n_s$ imaginary time slices the equal-time Green's function is recomputed from scratch.
  * `N_stab::Int`: Number of numerical stabilization intervals, $N_s = \left\lceil L_\tau / n_s \right\rceil.$
  * `N::Int`: Orbitals in system.
  * `β::E`: The inverse temperature $\beta=1/T,$ where $T$ is temperature.
  * `Δτ::E`: Discretization in imaginary time.
  * `Lτ::Int`: Length of imaginary time axis, $L_\tau = \beta / \Delta\tau.$
  * `B_bar::Vector{Matrix{T}}`: A multidimensional array where the matrix `B_bar[:,:,n]` represents $\bar{B}_n.$
  * `F::Vector{LDR{T,E}}`: A vector of $N_s$ LDR factorizations to represent the matrices $B(0,\tau)$ and $B(\tau,\beta)$.
  * `G′::Matrix{T}`: Matrix used for calculating the error corrected by numerical stabilization of the equal time Green's function.
  * `ldr_ws::LDRWorkspace{T}`: Workspace for performing LDR factorization while avoiding dynamic memory allocations.
