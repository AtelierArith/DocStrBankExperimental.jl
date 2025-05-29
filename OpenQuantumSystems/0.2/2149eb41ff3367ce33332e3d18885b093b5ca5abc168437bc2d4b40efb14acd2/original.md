```
master(W0, tspan, Ham; 
	reltol=1.0e-12, abstol=1.0e-12, int_reltol=1.0e-8, int_abstol=0.0, 
	fout=nothing, alg=DelayDiffEq.MethodOfSteps(DelayDiffEq.Vern6()))
```

Integrate Quantum Master equation 

$\frac{d}{d t} \rho(t) = - \frac{i}{\hbar} [ \hat{H}, \rho(t_0) ]  -\frac{1}{\hbar^2} \int_{t_0}^{t_1} \text{d} \tau \: [ \hat{H}, [ \hat{H}, \rho(\tau) ]]  ,\quad \hbar = 1.$

# Arguments

  * `W0`: Initial state vector (can be a bra or a ket) or initial propagator.
  * `tspan`: Vector specifying the points of time for which output should be displayed.s
  * `Ham`: Arbitrary operator specifying the Hamiltonian.
  * `reltol`: Relative tolerance for DiffEqCallbacks solver and its inner states.
  * `abstol`: Absolute tolerance for DiffEqCallbacks solver and its inner states.
  * `int_reltol`: Relative tolerance for QuadGK solver and its inner states.
  * `int_abstol`: Absolute tolerance for QuadGK solver and its inner states.
  * `fout=nothing`: If given, this function `fout(t, rho)` is called every time       an output should be displayed. ATTENTION: The state `rho` is neither       normalized nor permanent! It is still in use by the ode solver and       therefore must not be changed.
  * `alg`: Algorithm with which DiffEqCallbacks will solve QME equation.
