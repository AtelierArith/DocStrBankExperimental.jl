```julia
BacksolveAdjoint{CS, AD, FDT, VJP} <: AbstractAdjointSensitivityAlgorithm{CS, AD, FDT}
```

An implementation of adjoint sensitivity analysis using a backwards solution of the ODE. By default, this algorithm will use the values from the forward pass to perturb the backwards solution to the correct spot, allowing reduced memory (O(1) memory). Checkpointing stabilization is included for additional numerical stability over the naive implementation.

## Constructor

```julia
BacksolveAdjoint(; chunk_size = 0, autodiff = true,
    diff_type = Val{:central},
    autojacvec = nothing,
    checkpointing = true, noisemixing = false)
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
  * `checkpointing`: whether checkpointing is enabled for the reverse pass. Defaults to `true`.
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

## Applicability of Backsolve and Caution

When `BacksolveAdjoint` is applicable, it is a fast method, and requires the least memory. However, one must be cautious because not all ODEs are stable under backwards integration by the majority of ODE solvers. An example of such an equation is the Lorenz equation. Notice that if one solves the Lorenz equation forward and then in reverse with any adaptive time step and non-reversible integrator, then the backwards solution diverges from the forward solution. As a quick demonstration:

```julia
using Sundials
function lorenz(du, u, p, t)
    du[1] = 10.0 * (u[2] - u[1])
    du[2] = u[1] * (28.0 - u[3]) - u[2]
    du[3] = u[1] * u[2] - (8 / 3) * u[3]
end
u0 = [1.0; 0.0; 0.0]
tspan = (0.0, 100.0)
prob = ODEProblem(lorenz, u0, tspan)
sol = solve(prob, Tsit5(), reltol = 1e-12, abstol = 1e-12)
prob2 = ODEProblem(lorenz, sol.u[end], (100.0, 0.0))
sol = solve(prob, Tsit5(), reltol = 1e-12, abstol = 1e-12)
@show sol.u[end] - u0 #[-3.22091, -1.49394, 21.3435]
```

Thus, one should check the stability of the backsolve on their type of problem before enabling this method. Additionally, using checkpointing with backsolve can be a low memory way to stabilize it.

For more details on this topic, see [Stiff Neural Ordinary Differential Equations](https://aip.scitation.org/doi/10.1063/5.0060697).

## Checkpointing

To improve the numerical stability of the reverse pass, `BacksolveAdjoint` includes a checkpointing feature. If `sol.u` is a time series, then whenever a time `sol.t` is hit while reversing, a callback will replace the reversing ODE portion with `sol.u[i]`. This nudges the solution back onto the appropriate trajectory and reduces the numerical caused by drift.

## SciMLProblem Support

This `sensealg` only supports `ODEProblem`s, `SDEProblem`s, and `RODEProblem`s. This `sensealg` supports callback functions (events).

### Disclaimer for `SDEProblem`s

The runtime of this algorithm is in O(n^2) for diagonal-noise SDEs until issue #854 is solved.

## References

ODE: Rackauckas, C. and Ma, Y. and Martensen, J. and Warner, C. and Zubov, K. and Supekar, R. and Skinner, D. and Ramadhana, A. and Edelman, A., Universal Differential Equations for Scientific Machine Learning,	arXiv:2001.04385

Hindmarsh, A. C. and Brown, P. N. and Grant, K. E. and Lee, S. L. and Serban, R. and Shumaker, D. E. and Woodward, C. S., SUNDIALS: Suite of nonlinear and differential/algebraic equation solvers, ACM Transactions on Mathematical Software (TOMS), 31, pp:363–396 (2005)

Chen, R.T.Q. and Rubanova, Y. and Bettencourt, J. and Duvenaud, D. K., Neural ordinary differential equations. In Advances in neural information processing systems, pp. 6571–6583 (2018)

Pontryagin, L. S. and Mishchenko, E.F. and Boltyanskii, V.G. and Gamkrelidze, R.V. The mathematical theory of optimal processes. Routledge, (1962)

Rackauckas, C. and Ma, Y. and Dixit, V. and Guo, X. and Innes, M. and Revels, J. and Nyberg, J. and Ivaturi, V., A comparison of automatic differentiation and continuous sensitivity analysis for derivatives of differential equation solutions, arXiv:1812.01892

DAE: Cao, Y. and Li, S. and Petzold, L. and Serban, R., Adjoint sensitivity analysis for differential-algebraic equations: The adjoint DAE system and its numerical solution, SIAM journal on scientific computing 24 pp: 1076-1089 (2003)

SDE: Gobet, E. and Munos, R., Sensitivity Analysis Using Ito-Malliavin Calculus and Martingales, and Application to Stochastic Optimal Control, SIAM Journal on control and optimization, 43, pp. 1676-1713 (2005)

Li, X. and Wong, T.-K. L.and Chen, R. T. Q. and Duvenaud, D., Scalable Gradients for Stochastic Differential Equations, PMLR 108, pp. 3870-3882 (2020), http://proceedings.mlr.press/v108/li20i.html
