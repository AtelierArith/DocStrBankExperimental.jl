```
runcircuit(
  M::Union{MPS,MPO},
  circuit_tensors::Vector{<:ITensor};
  apply_dag=nothing,
  cutoff=1e-15,
  maxdim=10_000,
  svd_alg="divide_and_conquer",
  move_sites_back::Bool=true,
  kwargs...)
```

Apply a set of "gate" tensors (alredy in the form of `ITensor`) to an input state `M`, with options:

  * `apply_dag = nothing`: whether to perform conjugate evolution.
  * `cutoff = 1e-15`: truncation cutoff in SVD.
  * `maxdim = 10_000`: maximum bond dimension at SVD trunctions.
  * `svd_alg = "divide_and_conquer"`: SVD algorithm (see ITensors.jl).
  * `move_sites_back = true`: move sites back after long-range gate.

By default, `apply_dag = nothing` and the interface is dictated by the input state, and whether or not the vector of `ITensor` containins rank-3 noisy tensors (i.e. Kraus operators).

For an input MPS $|\psi_0\rangle$, with a unitary circuit, the output is

$$
|\psi\rangle = U_M\dots U_2 U_1|\psi_0\rangle
$$

while for noisy circuits:

$$
\rho = \mathcal{E}(|\psi_0\rangle\langle\psi_0|)
$$

For an input MPO $\rho_0$, the output is

$$
\rho = U_M\dots U_2 U_1 \rho_0 U^\dagger_1 U^\dagger_2,\dots,U^\dagger_M
$$

for unitary circuits, and $\rho = \mathcal{E}(\rho_0)$ for noisy circuits.
