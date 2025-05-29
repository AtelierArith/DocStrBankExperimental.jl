```julia
InterpolatingAdjoint{CS, AD, FDT, VJP} <: AbstractAdjointSensitivityAlgorithm{CS, AD, FDT}
```

An implementation of adjoint sensitivity analysis which uses the interpolation of the forward solution for the reverse solve vector-Jacobian products. By default it requires, a dense solution of the forward pass and will internally ignore saving arguments during the gradient calculation. When checkpointing is enabled, it will only require the memory to interpolate between checkpoints.

## Constructor

```julia
InterpolatingAdjoint(; chunk_size = 0, autodiff = true,
    diff_type = Val{:central},
    autojacvec = nothing,
    checkpointing = false, noisemixing = false)
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
  * `noisemixing`: Handle noise processes that are not of the form `du[i] = f(u[i])`. For example, to compute the sensitivities of an SDE with diagonal diffusion

    ```julia
    function g_mixing!(du, u, p, t)
        du[1] = p[3] * u[1] + p[4] * u[2]
        du[2] = p[3] * u[1] + p[4] * u[2]
        nothing
    end
    ```

    correctly, `noisemixing=true` must be enabled. The default is `false`.

For more details on the vjp choices, please consult the sensitivity algorithms documentation page or the docstrings of the vjp types.

## Checkpointing

To reduce the memory usage of the reverse pass, `InterpolatingAdjoint` includes a checkpointing feature. If `sol` is `dense`, checkpointing is ignored and the continuous solution is used for calculating `u(t)` at arbitrary time points. If `checkpointing=true` and `sol` is not `dense`, then dense intervals between `sol.t[i]` and `sol.t[i+1]` are reconstructed on-demand for calculating `u(t)` at arbitrary time points. This reduces the total memory requirement to only the cost of holding the dense solution over the largest time interval (in terms of number of required steps). The total compute cost is no more than double the original forward compute cost.

## SciMLProblem Support

This `sensealg` only supports `ODEProblem`s, `SDEProblem`s, and `RODEProblem`s. This `sensealg` supports callbacks (events).

### Disclaimer for `SDEProblem`s

The runtime of this algorithm is in O(n^2) for diagonal-noise SDEs until issue #854 is solved.

## References

Rackauckas, C. and Ma, Y. and Martensen, J. and Warner, C. and Zubov, K. and Supekar, R. and Skinner, D. and Ramadhana, A. and Edelman, A., Universal Differential Equations for Scientific Machine Learning,	arXiv:2001.04385

Hindmarsh, A. C. and Brown, P. N. and Grant, K. E. and Lee, S. L. and Serban, R. and Shumaker, D. E. and Woodward, C. S., SUNDIALS: Suite of nonlinear and differential/algebraic equation solvers, ACM Transactions on Mathematical Software (TOMS), 31, pp:363–396 (2005)

Rackauckas, C. and Ma, Y. and Dixit, V. and Guo, X. and Innes, M. and Revels, J. and Nyberg, J. and Ivaturi, V., A comparison of automatic differentiation and continuous sensitivity analysis for derivatives of differential equation solutions, arXiv:1812.01892
