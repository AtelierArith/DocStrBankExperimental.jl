```
NgIteration <: Method
```

Solves the system by recursive iteration in Fourier Space, and uses the Ng acceleration method. Essentially, the algorithm is:

1. guess an initial γ(r)
2. find c(r) using the closure relation
3. fourier transform to get ĉ(k)
4. find γ(k) using the OZ-eq in k-space
5. compute γ(r) with a inverse fourier transform
6. use Ng's method to provide a next guess for γ
7. compare with previous value, if not converged go to 2.

Arguments:

  * `M::Int`: number of points discretize the solution on
  * `dr::Float64`: grid spacing in real space
  * `N_stages::Int`: Number of previous values to take into account for step 6. A higher number should lead to faster convergence, yet more computation time per iteration.
  * `max_iterations::Int64`: maximal number of iterations
  * `tolerance::Float64`: tolerance to be reached
  * `verbose::Bool`: whether or not to print convergence information

Default: `NgIteration(; N_stages=3, max_iterations=10^3, tolerance=10^-6, verbose=true, M=1000, dr=10.0/M)`

References: Ng, K. C. (1974). Hypernetted chain solutions for the classical one‐component plasma up to Γ= 7000. The Journal of Chemical Physics, 61(7), 2680-2689.
