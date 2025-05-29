```
getsamples(M::Union{MPS,MPO,ITensor}, bases::Matrix::Matrix{<:String}, nshots::int; kwargs...)
getsamples(M::Union{MPS,MPO,ITensor}, bases::Vector{<:Vector}, nshots::Int; kwargs...) =
```

Generate a set of measurements acccording to a set of input `bases`, performing `nshots` measurements per basis. For a single measurement, a depth-1 unitary $U$ is applied to the input state $M$ according to the `basis`. The probability of recording outcome $\sigma = (\sigma_1,\sigma_2,\dots)$ in the basis defined by $U$ is

  * $P(\sigma) = |\langle\sigma|U\psi\rangle|^2$,   if $M = |\psi\rangle$ is an `MPS`.
  * $P(\sigma) = \langle\sigma|U\rho U^\dagger|\sigma\rangle$,   if $M = \rho$ is an `MPO`.
