```
pclqofc_hr(psys, Q, R, nh = 0; K = 1, sdeg = 0, G = I, vinit, optimizer, stabilizer,
           maxiter, vtol, Jtol, gtol, show_trace, solver, reltol, abstol, 
           N = 128, quad = false ) -> (Fopt,info)
```

Compute the optimal periodic stabilizing gain matrix `Fopt(t)`, such that for a continuous-time periodic state-space model  `psys` of the form

```
  .
  x(t) = A(t)x(t) + B(t)u(t) + Bw(t)w(t)  
  y(t) = C(t)x(t) + D(t)u(t) + Dw(t)w(t) ,
```

the output feedback control law

```
u(t) = Fopt(t)*y(t),
```

minimizes the expectation of the quadratic index

```
         ∞
 J = E{ Int [x(t)'*Q(t)*x(t) + u(t)'*R(t)*u(t)]dt },
        t=0
```

where `Q(t)` and `R(t)` are periodic weighting matrices.  The matrices of the system `psys` are of type `HarmonicArray`.  For a system of order `n` with `m` control inputs in `u(t)` and `p` measurable outputs in `y(t)`,  `Q(t)` and `R(t)` are `n×n` and `m×m` symmetric periodic matrices of type `HarmonicArray`, respectively.                 The dimension `m` of `u(t)` is deduced from the dimension of `R(t)`.  `Q` and `R` can be alternatively provided as constant real matrices. 

The resulting `m×p` periodic output feedback gain `Fopt(t)` is of type `HarmonicArray` and is computed as `Fopt(t) = inv(I+F(t)D(t))*F(t)`, with `F(t)` in the harmonic representation form 

```
              nh
 F(t) = F0 +  ∑ ( Fc_i*cos(i*t*2*π/T)+Fs_i*sin(i*2*π*t/T) ) ,
             i=1
```

where `T` is the system period, `F0` is the constant term, `Fc_i` is the `i`-th cosinus coefficient matrix and `Fs_i` is the `i`-th sinus coefficient matrix.  By default, the number of harmonics is `nh = 0` (i.e., constant output feedback is used).

The covariance matrix of the initial state `x(0)` can be specified via the keyword argument `G` (default: `G = I`) and a desired stability degree of the closed-loop characteristic exponents can be specified using the keyword argument `sdeg` (default: `sdeg = 0`). 

For the determination of the optimal feedback gains `F0`, `Fc_i` and `Fs_i` for `i = 1, ...., nh` an optimization-based approach is employed using  tools available in the optimization package [`Optim.jl`](https://github.com/JuliaNLSolvers/Optim.jl).  By default, the gradient-based limited-memory quasi-Newton method (also known as `L-BFGS`) for unconstrained minimizations  is employed using the keyword argument setting `optimizer = LBFGS(;alphaguess = LineSearches.InitialStatic(;scaled=true))`, where  an initial step length for the line search algorithm is chosen using the keyword argument `alphaguess`  (see the [`LineSearches.jl`](https://github.com/JuliaNLSolvers/LineSearches.jl) package for alternative options).  The employed default line search algorithm is `HagerZhang()` and an alternative method can be specified using the keyword argument `linesearch`  (e.g., `linesearch = LineSearches.MoreThuente()`).   Alternative gradient-based methods can be also selected, such as, for example,  the quasi-Newton method `BFGS` with `optimizer = Optim.BFGS()`, or  for small size optimization problems, the Nelder-Mead gradient-free method with `optimizer = Optim.NelderMead()`.  For the computation of the function `J` and its gradient  `∇J`, the formulas developed in [1] for stable systems are used. Each evaluation involves the solution of  of a pair of periodic Lyapunov differential equations using single or multiple shooting methods proposed in [2].   If the original system `psys` is unstable, the computation of a stabilizing feedback is performed using the same optimization techniques applied iteratively to systems  with modified the state matrices of the form  `A(t)-αI`, where `α ≥ 0` is chosen such that `A(t)-αI` is stable, and the values of `α` are successively decreased until the stabilization is achieved. The optimization method for stabilization can be independently selected using the keyword argument `stabilizer`, with the default setting   `stabilizer = LBFGS(;alphaguess = LineSearches.InitialStatic(;scaled=true))`. If only stabilization is desired, then use  `optimizer = nothing`. 

An internal optimization variable `v` is used, formed as an `m*p*(2*nh+1)` dimensional vector `v := [vec(F0); vec(Fc_1); vec(Fs_1), ... ; vec(Kc_nh); vec(Ks_nh)]'.  By default,`v`is initialized as`v = 0`(i.e., a zero vector of appropriate dimension).  The keyword argument`vinit = v0`can be used to initialize`v`with an arbitrary vector`v0`.   

The optimization process is controlled using several keyword parameters.  The keyword parameter `maxiter = maxit` can be used to specify the maximum number of iterations to be performed (default: `maxit = 1000`). The keyword argument `vtol` can be used to specify the absolute tolerance in  the changes of the optimization variable `v` (default: `vtol = 0`). The keyword argument `Jtol` can be used to specify the relative tolerance in the changes of the optimization criterion `J` (default: `Jtol = 0`),  while `gtol` can be used to specify the absolute tolerance in the gradient  `∇J`, in infinity norm (default: `gtol = 1e-5`).  With the keyword argument `show_trace = true`,  a trace of the optimization algorithm's state is shown on `stdout` (default `show_trace = false`).    For stabilization purposes,  the values `Jtol = 1.e-3`, `gtol = 1.e-2`, `maxit = 20` are used to favor faster convergence. 

The returned named tuple `info` contains `(fopt, sdeg0, sdeg, vopt, optres)`, where:

`info.fopt` is the resulting value of the optimal performance `J`;

`info.sdeg0` is the initial stability degree of the closed-loop characteristic exponents;

`info.sdeg` is the resulting stability degree of the closed-loop characteristic exponents;

`info.vopt` is the resulting value of the optimization variable `v`; 

`info.optres` is the result returned by the `Optim.optimize(...)` function of the  [`Optim.jl`](https://github.com/JuliaNLSolvers/Optim.jl) package;  several functions provided by this package can be used to inquire various information related to the optimization results (see the documention of this package). 

Several keyword arguments can be used to control the integration of the involved ODE's for the solution of  periodic differential Lyapunov equations for function and gradient evaluations. 

If `K = 1` (default), the single shooting method is employed to compute periodic generators [1].  If `K > 1`, the multiple-shooting method of [2] is employed, first, to convert the continuous-time periodic Lyapunov differential equations into discrete-time periodic Lyapunov equations satisfied by  the generator solution in `K` grid points and then to compute the solution by solving an appropriate discrete-time periodic Lyapunov  equation using the periodic Schur method of [3]. If quad = true, a quadrature-based evaluation of gradients is used, as proposed in [1], in conjunction with interpolation techniques. The number of sample values to be used for interpolation can be specified with the keyword parameter `N` (deafult: `N = 128`). 

The ODE solver to be employed to convert the continuous-time problem into a discrete-time problem can be specified using the keyword argument `solver`,  together with the required relative accuracy `reltol` (default: `reltol = 1.e-4`),   absolute accuracy `abstol` (default: `abstol = 1.e-7`) and stepsize `dt` (default: `dt = 0`, only used if `solver = "symplectic"`).  Depending on the desired relative accuracy `reltol`, lower order solvers are employed for `reltol >= 1.e-4`,  which are generally very efficient, but less accurate. If `reltol < 1.e-4`, higher order solvers are employed able to cope with high accuracy demands. 

The following solvers from the [OrdinaryDiffEq.jl](https://github.com/SciML/OrdinaryDiffEq.jl) package can be selected:

`solver = "non-stiff"` - use a solver for non-stiff problems (`Tsit5()` or `Vern9()`);

`solver = "stiff"` - use a solver for stiff problems (`Rodas4()` or `KenCarp58()`);

`solver = "auto"` - use the default solver, which automatically detects stiff problems (`AutoTsit5(Rosenbrock23())` or `AutoVern9(Rodas5())`). 

Parallel computation of the matrices of the discrete-time problem can be alternatively performed  by starting Julia with several execution threads.  The number of execution threads is controlled either by using the `-t/--threads` command line argument  or by using the `JULIA_NUM_THREADS` environment variable. 

[1] L. Vigano, M. Bergamasco, M. Lovera, and A. Varga. Optimal periodic output feedback control: a continuous-time approach and a case study.     Int. J. Control, Vol. 83, pp. 897–914, 2010.  

[2] A. Varga. On solving periodic differential matrix equations with applications to periodic system norms computation.      Proc. IEEE CDC/ECC, Seville, 2005. 

[3] A. Varga. Periodic Lyapunov equations: some applications and new algorithms.      Int. J. Control, vol, 67, pp, 69-87, 1997.
