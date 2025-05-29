```
getsamples(M::Union{MPS,MPO}, nshots::Int; kwargs...)
getsamples(T::ITensor, nshots::Int)
```

Perform `nshots` projective measurements of a wavefunction $|\psi\rangle$ or density operator $\rho$ in the MPS/MPO reference basis. Each measurement consists of a binary vector $\sigma = (\sigma_1,\sigma_2,\dots)$, drawn from the probabilty distributions:

  * $P(\sigma) = |\langle\sigma|\psi\rangle|^2$,   if $M = |\psi\rangle$ is an `MPS`.
  * $P(\sigma) = \langle\sigma|\rho|\sigma\rangle$   :  if $M = \rho$ is an `MPO`.
