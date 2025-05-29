```julia
ForwardSensitivity{CS, AD, FDT} <: AbstractForwardSensitivityAlgorithm{CS, AD, FDT}
```

An implementation of continuous forward sensitivity analysis for propagating derivatives by solving the extended ODE. When used within adjoint differentiation (i.e. via Zygote), this will cause forward differentiation of the `solve` call within the reverse-mode automatic differentiation environment.

## Constructor

```julia
ForwardSensitivity(;
    chunk_size = 0, autodiff = true,
    diff_type = Val{:central},
    autojacvec = autodiff,
    autojacmat = false)
```

## Keyword Arguments

  * `autodiff`: Use automatic differentiation in the internal sensitivity algorithm computations. Default is `true`.
  * `chunk_size`: Chunk size for forward mode differentiation if full Jacobians are built (`autojacvec=false` and `autodiff=true`). Default is `0` for automatic choice of chunk size.
  * `autojacvec`: Calculate the Jacobian-vector product via automatic differentiation with special seeding.
  * `diff_type`: The method used by FiniteDiff.jl for constructing the Jacobian if the full Jacobian is required with `autodiff=false`.

Further details:

  * If `autodiff=true` and `autojacvec=true`, then the one chunk `J*v` forward-mode directional derivative calculation trick is used to compute the product without constructing the Jacobian (via ForwardDiff.jl).
  * If `autodiff=false` and `autojacvec=true`, then the numerical direction derivative trick `(f(x+epsilon*v)-f(x))/epsilon` is used to compute `J*v` without constructing the Jacobian.
  * If `autodiff=true` and `autojacvec=false`, then the Jacobian is constructed via chunked forward-mode automatic differentiation (via ForwardDiff.jl).
  * If `autodiff=false` and `autojacvec=false`, then the Jacobian is constructed via finite differences via FiniteDiff.jl.

## SciMLProblem Support

This `sensealg` only supports `ODEProblem`s without callbacks (events).
