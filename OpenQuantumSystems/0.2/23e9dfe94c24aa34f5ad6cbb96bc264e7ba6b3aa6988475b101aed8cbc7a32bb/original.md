```
MemoryKernel_4_traced(H_II_t, H_II_tau, W_bath, agg, FCProd, aggIndices, indicesMap)
```

Calculate the fourth part of Memory Kernel with the definition

$\mathcal{M}_1(t, \tau) = \operatorname{tr}_B \{ W_\text{bath} \hat{H}_I^{(I)}(t) \hat{H}_I^{(I)}(\tau) \}$.

# Arguments

  * `H_II_t`: Interaction Hamiltonian in interaction picutre at the time t, $\hat{H}_I^{(I)}(t)$.
  * `H_II_tau`: Interaction Hamiltonian in interaction picutre at the time `tau`, $\hat{H}_I^{(I)}(\tau)$.
  * `W_bath`: Density matrix representing bath part of the density matrix, see [`get_rho_bath`](@ref).
  * `agg`: Aggregate of molecules, see [`Aggregate`](@ref).
  * `aggIndices`: Aggregate indices, see [`getIndices`](@ref).
  * `indicesMap`: Aggregate vibrational indices, see [`getVibIndices`](@ref).
