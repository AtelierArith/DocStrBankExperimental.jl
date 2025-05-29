```
KrylovMethod(;
    type = Val(Krylov.GmresSolver),
    jacobian_free_jvp = nothing,
    forcing_term = ConstantForcing(0),
    args = (20,),
    kwargs = (;),
    solve_kwargs = (;),
    disable_preconditioner = false,
    verbose = Silent(),
    debugger = nothing,
)
```

Finds an approximation `Δx[n] ≈ j(x[n]) \ f(x[n])` for Newton's method such that `‖f(x[n]) - j(x[n]) * Δx[n]‖ ≤ rtol[n] * ‖f(x[n])‖`, where `rtol[n]` is the value of the forcing term on iteration `n`. This is done by calling `solve_krylov!(::KrylovMethod, cache, Δx, x, f!, f, n, prepare_for_f!, j = nothing)`, where `f` is `f(x[n])` and, if it is specified, `j` is either `j(x[n])` or an approximation of `j(x[n])`. The `Δx` passed to a Krylov method is modified in-place. The `cache` can be obtained with `allocate_cache(::KrylovMethod, x_prototype)`, where `x_prototype` is `similar` to `x` (and also to `Δx` and `f`).

This is primarily a wrapper for a `Krylov.KrylovSolver` from `Krylov.jl`. In `allocate_cache`, the solver is constructed with `solver = type(l, l, args..., Krylov.ktypeof(x_prototype); kwargs...)`, where `l = length(x_prototype)` and `Krylov.ktypeof(x_prototype)` is a subtype of `DenseVector` that can be used to store `x_prototype`. By default, the solver is a `Krylov.GmresSolver` with a Krylov subspace size of 20 (the default Krylov subspace size for this solver in `Krylov.jl`). In `solve_krylov!`, the solver is run with `Krylov.solve!(solver, opj, f; M, ldiv, atol, rtol, verbose, solve_kwargs...)`. The solver's type can be changed by specifying a different value for `type`, though this value has to be wrapped in a `Val` to avoid runtime compilation.

In the call to `Krylov.solve!`, `opj` is a `LinearOperator` that represents `j(x[n])`, which the solver uses by evaluating `mul!(jΔx, opj, Δx)`. If a Jacobian-free JVP (Jacobian-vector product) is specified, it gets used to construct `opj` and to evaluate the calls to `mul!`; otherwise, `j` itself gets used to construct `opj`, and the calls to `mul!` simplify to `mul!(jΔx, j, Δx)`.

If a Jacobian-free JVP and `j` are both specified, and if `disable_preconditioner` is set to `false`, `j` is treated as an approximation of `j(x[n])` and is used as the (left) preconditioner `M` in order to speed up the solver; otherwise, the preconditioner is simply set to the identity matrix `I`. The keyword argument `ldiv` is set to `true` so that the solver calls `ldiv!(Δx′, M, f′)` instead of `mul!(Δx′, M, f′)`, where `Δx′` and `f′` denote internal variables of the solver that roughly correspond to `Δx` and `f`. In other words, setting `ldiv` to `true` makes the solver treat `M` as an approximation of `j` instead of as the inverse of an approximation of `j`.

The keyword argument `atol` is set to 0 because, if it is set to some other value, the inequality `‖f(x[n]) - j(x[n]) * Δx[n]‖ ≤ rtol[n] * ‖f(x[n])‖` changes to `‖f(x[n]) - j(x[n]) * Δx[n]‖ ≤ rtol[n] * ‖f(x[n])‖ + atol`, which eliminates any convergence guarantees provided by the forcing term (in order for the Newton-Krylov method to converge, the right-hand side of this inequality must approach 0 as `n` increases, which cannot happen if `atol` is not 0).

All of the arguments and keyword arguments used to construct and run the solver can be modified using `args`, `kwargs`, and `solve_kwargs`. So, the default behavior of this wrapper can be easily overwritten, and any features of `Krylov.jl` that are not explicitly covered by this wrapper can still be used.

If `verbose` is `true`, the residual `‖f(x[n]) - j(x[n]) * Δx[n]‖` is printed on each iteration of the Krylov method. If a debugger is specified, it is run before the call to `Kyrlov.solve!`.
