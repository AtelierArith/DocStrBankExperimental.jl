```
schroedinger_dynamic(psi0, tspan, f; 
	reltol=1.0e-12, abstol=1.0e-12, fout=nothing, alg=OrdinaryDiffEq.Tsit5())
```

Integrate time-dependent Schroedinger equation to evolve states or compute propagators

$\frac{d}{d t}\vert\psi(t)\rangle = - \frac{i}{\hbar} \hat H(t)\vert\rho(t)\rangle, \quad \hbar = 1$.

# Arguments

  * `psi0`: Initial state vector (can be a bra or a ket) or initial propagator.
  * `tspan`: Vector specifying the points of time for which output should be displayed.
  * `f`: Function `f(t, psi) -> H` returning the time and or state dependent Hamiltonian.
  * `reltol`: Relative tolerance for OrdinaryDiffEq solver and its inner states.
  * `abstol`: Absolute tolerance for OrdinaryDiffEq solver and its inner states.
  * `fout=nothing`: If given, this function `fout(t, psi)` is called every time       an output should be displayed. ATTENTION: The state `psi` is neither       normalized nor permanent! It is still in use by the ode solver and       therefore must not be changed.
  * `alg`: Algorithm with which OrdinaryDiffEq will solve Schroedinger equation.
