```julia
GaussAdjoint{CS, AD, FDT, VJP} <: AbstractAdjointSensitivityAlgorithm{CS, AD, FDT}
```

An implementation of adjoint sensitivity analysis which solves the quadrature during the reverse solve with a callback, thus not requiring a dense adjoint solution. This method requires the dense forward solution and will ignore saving arguments during the gradient calculation. The tolerances in the constructor control the inner quadrature.

This method is O(n^3 + p) for stiff / implicit equations (as opposed to the O((n+p)^3) scaling of BacksolveAdjoint and InterpolatingAdjoint), and thus is much more compute efficient. It also does not requires holding a dense reverse pass and is thus memory efficient.

## Constructor

```julia
GaussAdjoint(; chunk_size = 0, autodiff = true,
    diff_type = Val{:central},
    autojacvec = nothing,
    checkpointing = false)
```

## Keyword Arguments

  * `autodiff`: Use automatic differentiation for constructing the Jacobian if the Jacobian needs to be constructed.  Defaults to `true`.
  * `chunk_size`: Chunk size for forward-mode differentiation if full Jacobians are built (`autojacvec=false` and `autodiff=true`). Default is `0` for automatic choice of chunk size.
  * `diff_type`: The method used by FiniteDiff.jl for constructing the Jacobian if the full Jacobian is required with `autodiff=false`.
  * `autojacvec`: Calculate the vector-Jacobian product (`J'*v`) via automatic differentiation with special seeding. The total set of choices are:

      * `nothing`: uses an automatic algorithm to automatically choose the vjp. This is the default and recommended for most users.
      * `false`: the Jacobian is constructed via FiniteDiff.jl
      * `true`: the Jacobian is constructed via ForwardDiff.jl
      * `TrackerVJP`: Uses Tracker.jl for the vjp.
      * `ZygoteVJP`: Uses Zygote.jl for the vjp.
      * `EnzymeVJP`: Uses Enzyme.jl for the vjp.
      * `ReverseDiffVJP(compile=false)`: Uses ReverseDiff.jl for the vjp. `compile` is a boolean for whether to precompile the tape, which should only be done if there are no branches (`if` or `while` statements) in the `f` function.
  * `checkpointing`: whether checkpointing is enabled for the reverse pass. Defaults to `false`.

For more details on the vjp choices, please consult the sensitivity algorithms documentation page or the docstrings of the vjp types.

## SciMLProblem Support

This `sensealg` only supports `ODEProblem`s. This `sensealg` supports events (callbacks).

## References

Rackauckas, C. and Ma, Y. and Martensen, J. and Warner, C. and Zubov, K. and Supekar, R. and Skinner, D. and Ramadhana, A. and Edelman, A., Universal Differential Equations for Scientific Machine Learning,	arXiv:2001.04385

Hindmarsh, A. C. and Brown, P. N. and Grant, K. E. and Lee, S. L. and Serban, R. and Shumaker, D. E. and Woodward, C. S., SUNDIALS: Suite of nonlinear and differential/algebraic equation solvers, ACM Transactions on Mathematical Software (TOMS), 31, pp:363–396 (2005)

Rackauckas, C. and Ma, Y. and Dixit, V. and Guo, X. and Innes, M. and Revels, J. and Nyberg, J. and Ivaturi, V., A comparison of automatic differentiation and continuous sensitivity analysis for derivatives of differential equation solutions, arXiv:1812.01892

Kim, S., Ji, W., Deng, S., Ma, Y., & Rackauckas, C. (2021). Stiff neural ordinary differential equations. Chaos: An Interdisciplinary Journal of Nonlinear Science, 31(9), 093122.
