```
FourierIteration <: Method
```

Solves the system by recursive iteration in Fourier Space. Essentially, the algorithm is:

1. guess an initial γ(r)
2. find c(r) using the closure relation
3. fourier transform to get ĉ(k)
4. find γ(k) using the OZ-eq in k-space
5. compute γ(r) with a inverse fourier transform
6. compare with previous value, if not converged go to 2.

Optionally, a mixing rule is used to mix the new and previous iteration of c(r) in step 2. 

Arguments:

  * `M::Int`: number of points discretize the solution on
  * `dr::Float64`: grid spacing in real space
  * `mixing_parameter::Float64`: mixing parameter for iteration mixing. A value of 1 is no mixing. Must be between 0 and 1.
  * `max_iterations::Int64`: maximal number of iterations
  * `tolerance::Float64`: tolerance to be reached
  * `verbose::Bool`: whether or not to print convergence information

Default: `FourierIteration(; mixing_parameter=0.5, max_iterations=10^5, tolerance=10^-6, verbose=true, M=1000, dr=10.0/M)`
