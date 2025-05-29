```
liouvilleVonNeumann(rho0, tspan, H; 
	reltol=1.0e-12, abstol=1.0e-12, fout=nothing, alg=OrdinaryDiffEq.Tsit5())
```

Integrate Liouville-von Neumann equation to evolve states or compute propagators

$\frac{d}{d t} \rho(t) = - \frac{i}{\hbar} [ \hat H, \rho(t) ], \quad \hbar = 1$.

# Arguments

  * `rho0`: Initial state vector (can be a bra or a ket) or initial propagator.
  * `tspan`: Vector specifying the points of time for which output should be displayed.
  * `H`: Arbitrary operator specifying the Hamiltonian.
  * `reltol`: Relative tolerance for OrdinaryDiffEq solver and its inner states.
  * `abstol`: Absolute tolerance for OrdinaryDiffEq solver and its inner states.
  * `fout=nothing`: If given, this function `fout(t, rho)` is called every time       an output should be displayed. ATTENTION: The state `rho` is neither       normalized nor permanent! It is still in use by the ode solver and       therefore must not be changed.
  * `alg`: Algorithm with which OrdinaryDiffEq will solve LvN equation.
