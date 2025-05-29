```
PowerSpectrum(M, ρ, P_op, Q_op, ωlist, reverse; solver, verbose, filename, SOLVEROptions...)
```

Calculate power spectrum for the system in frequency domain.

$$
\pi S(\omega)=\textrm{Re}\left\{\int_0^\infty dt \langle P(t) Q(0)\rangle e^{-i\omega t}\right\},
$$

# To calculate spectrum when input operator `Q_op` has `EVEN`-parity:

remember to set the parameters: 

  * `M::AbstractHEOMLSMatrix`: should be `EVEN` parity

# To calculate spectrum when input operator `Q_op` has `ODD`-parity:

remember to set the parameters: 

  * `M::AbstractHEOMLSMatrix`: should be `ODD` parity

# Parameters

  * `M::AbstractHEOMLSMatrix` : the HEOMLS matrix.
  * `ρ::Union{QuantumObject,ADOs}` :  the system density matrix or the auxiliary density operators.
  * `P_op::Union{QuantumObject,HEOMSuperOp}`: the system operator (or `HEOMSuperOp`) $P$ acting on the system.
  * `Q_op::Union{QuantumObject,HEOMSuperOp}`: the system operator (or `HEOMSuperOp`) $Q$ acting on the system.
  * `ωlist::AbstractVector` : the specific frequency points to solve.
  * `reverse::Bool` : If `true`, calculate $\langle P(-t)Q(0) \rangle = \langle P(0)Q(t) \rangle = \langle P(t)Q(0) \rangle^*$ instead of $\langle P(t) Q(0) \rangle$. Default to `false`.
  * `solver::SciMLLinearSolveAlgorithm` : solver in package `LinearSolve.jl`. Default to `KrylovJL_BICGSTAB(rtol=1e-12, atol=1e-14)`.
  * `verbose::Bool` : To display verbose output and progress bar during the process or not. Defaults to `true`.
  * `filename::String` : If filename was specified, the value of spectrum for each ω will be saved into the file "filename.txt" during the solving process.
  * `SOLVEROptions` : extra options for solver

# Notes

  * For more details about `solver` and `SOLVEROptions`, please refer to [`LinearSolve.jl`](http://linearsolve.sciml.ai/stable/)

# Returns

  * `spec::AbstractVector` : the spectrum list corresponds to the specified `ωlist`
