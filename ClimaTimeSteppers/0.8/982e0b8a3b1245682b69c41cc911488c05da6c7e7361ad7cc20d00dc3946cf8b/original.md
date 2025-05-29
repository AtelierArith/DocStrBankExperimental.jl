```
NewtonsMethod(;
    max_iters = 1,
    update_j = UpdateEvery(NewNewtonIteration),
    krylov_method = nothing,
    convergence_checker = nothing,
    verbose = Silent(),
)
```

Solves the equation `f(x) = 0`, using the Jacobian (or an approximation of the Jacobian) `j(x) = f'(x)` if it is available. This is done by calling `solve_newton!(::NewtonsMethod, cache, x, f!, j! = nothing)`, where `f!(f, x)` is a function that sets `f(x)` in-place and, if it is specified, `j!(j, x)` is a function that sets `j(x)` in-place. The `x` passed to Newton's method is modified in-place, and its initial value is used as a starting guess for the root. The `cache` can be obtained with `allocate_cache(::NewtonsMethod, x_prototype, j_prototype = nothing)`, where `x_prototype` is `similar` to `x` and `f(x)`, and, if it is specified, `j_prototype` is `similar` to `j(x)`. In order for `j(x)` to be invertible, it must be a square matrix, which implies that `x` and `f(x)` must be `similar` to to each other.

Let `x[n]` denote the value of `x` on the `n`-th Newton iteration (with `x[0]` denoting the initial value of `x`), and suppose that `x[n]` is sufficiently close to some root `x̂` of `f(x)` to make the first-order approximation     `f(x̂) ≈ f(x[n]) + j(x[n]) * (x̂ - x[n])`. Since `f(x̂) = 0`, the error on the `n`-th iteration is roughly     `x[n] - x̂ ≈ Δx[n]`, where `Δx[n] = j(x[n]) \ f(x[n])`. Newton's method sets `x[n + 1]` to be the value of `x̂` given by this approximation:     `x[n + 1] = x[n] - Δx[n]`.

If a Krylov method is specified, it gets used to compute the error `Δx[n] = j(x[n]) \ f(x[n])`; otherwise, the error is directly computed by calling `ldiv!(Δx, j, f)`. If the Krylov method uses a Jacobian-free JVP (Jacobian-vector product), `j_prototype` and `j!` do not need to be specified. When Newton's method uses a Krylov method, it is called a "Newton-Krylov method"; furthermore, when the Krylov method uses a Jacobian-free JVP, it is called a "Jacobian-free Newton-Krylov method".

If `j_prototype` is specified, it should not be an `DenseMatrix`. If it is, it has to be factorized with `lu` before `ldiv!` is called, which requires the allocation of additional memory. Instead, `j_prototype` should be an object that can directly be passed to `ldiv!`. For convenience, though, the use of an `DenseMatrix` is supported. However, `Krylov.jl` does not provide such support for its preconditioners, so, since the value computed with `j!` is used as a preconditioner in Krylov methods with a Jacobian-free JVP, using such a Krylov method requires specifying a `j_prototype` that can be passed to `ldiv!`.

If `j(x)` changes sufficiently slowly, `update_j` may be changed from `UpdateEvery(NewNewtonIteration)` to some other `UpdateSignalHandler` that gets triggered less frequently, such as `UpdateEvery(NewNewtonSolve)`. This can be used to make the approximation `j(x[n]) ≈ j(x₀)`, where `x₀` is a previous value of `x[n]` (possibly even a value from a previous `solve_newton!` of Newton's method). When Newton's method uses such an approximation, it is called the "chord method".

In addition, `update_j` can be set to an `UpdateSignalHandler` that gets triggered by signals that originate outside of Newton's method, such as `UpdateEvery(NewTimeStep)`. It is possible to send any signal for updating `j` to Newton's method while it is not running by calling `update!(::NewtonsMethod, cache, ::UpdateSignal, j!)`, where in this case `j!(j)` is a function that sets `j` in-place without any dependence on `x` (since `x` is not necessarily defined while Newton's method is not running, this version of `j!` does not take `x` as an argument). This can be used to make the approximation `j(x[n]) ≈ j₀`, where `j₀` can have an arbitrary value.

If a convergence checker is provided, it gets used to determine whether to stop iterating on iteration `n` based on the value `x[n]` and its error `Δx[n]`; otherwise, Newton's method iterates from `n = 0` to `n = max_iters`. If the convergence checker determines that `x[n]` has not converged by the time `n = max_iters`, a warning gets printed.

If `verbose` is set to `true`, the norms of `x[n]` and `Δx[n]` get printed on every iteration. If there is no convergence checker, `Δx[n]` is not computed on the last iteration, so its final norm is not printed.
