```
waveguide_evolution(tspan, psi0, H; fout)
```

Integrate time-dependent Schroedinger equation to evolve states or compute propagators.

# Arguments

  * `tspan`: Vector specifying the points of time for which output should be displayed.
  * `psi0`: Initial state vector can only be a ket.
  * `H`: Operator containing a [`WaveguideOperator`](@ref) either through a LazySum or LazyTensor.
  * `fout=nothing`: If given, this function `fout(t, psi)` is called every time step. Example: `fout(t,psi) = expect(A,psi)` will return the epectation value of A at everytimestep.  If `fout =1` the state psi is returned for all timesteps in a vector.  ATTENTION: The state `psi` is neither normalized nor permanent! It is still in use by the ode solver and therefore must not be changed.

# Returns

  * if `fout=nothing` the output of the solver will be the state `ψ` at the last timestep.
  * if `fout` is given a tuple with the state `ψ` at the last timestep and the output of `fout` is given. If `fout` returns a tuple the tuple will be flattened.
  * if `fout = 1` `ψ` at all timesteps is returned.

# Examples

  * `fout(t,psi) = (expect(A,psi),expect(B,psi))` will result in  a tuple (ψ, ⟨A(t)⟩,⟨B(t)⟩), where `⟨A(t)⟩` is a vector with the expectation value of `A` as a function of time.
