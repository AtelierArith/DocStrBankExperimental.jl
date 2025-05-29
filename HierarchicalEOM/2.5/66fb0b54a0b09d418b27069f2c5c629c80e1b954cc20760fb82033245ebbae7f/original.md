```
DensityOfStates(M, ρ, d_op, ωlist; solver, verbose, filename, SOLVEROptions...)
```

Calculate density of states for the fermionic system in frequency domain.

$$
    \pi A(\omega)=\textrm{Re}\left\{\int_0^\infty dt \left[\langle d(t) d^\dagger(0)\rangle^* + \langle d^\dagger(t) d(0)\rangle \right] e^{-i\omega t}\right\},
$$

# Parameters

  * `M::AbstractHEOMLSMatrix` : the HEOMLS matrix which acts on `ODD`-parity operators.
  * `ρ::Union{QuantumObject,ADOs}` :  the system density matrix or the auxiliary density operators.
  * `d_op::QuantumObject` : The annihilation operator ($d$ as shown above) acting on the fermionic system.
  * `ωlist::AbstractVector` : the specific frequency points to solve.
  * `solver::SciMLLinearSolveAlgorithm` : solver in package `LinearSolve.jl`. Default to `KrylovJL_BICGSTAB(rtol=1e-12, atol=1e-14)`.
  * `verbose::Bool` : To display verbose output and progress bar during the process or not. Defaults to `true`.
  * `filename::String` : If filename was specified, the value of spectrum for each ω will be saved into the file "filename.txt" during the solving process.
  * `SOLVEROptions` : extra options for solver

# Notes

  * For more details about `solver` and `SOLVEROptions`, please refer to [`LinearSolve.jl`](http://linearsolve.sciml.ai/stable/)

# Returns

  * `dos::AbstractVector` : the list of density of states corresponds to the specified `ωlist`
