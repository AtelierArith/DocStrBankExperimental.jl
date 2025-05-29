```
optimize!(
    fdf, M::OptBuffer, x₀;
    gtol=1e-6,
    convcond=nothing,
    maxiter=100,
    maxcalls=nothing,
    reset=true,
    constrain_step=nothing,
    tracking=nothing,
    verbosity=0
)
```

Find an optimizer for `fdf`, starting with the initial approximation `x₀`.

# Arguments

  * `M::OptBuffer`: the core method to use for optimization
  * `fdf(x, g)::Function`: function to optimize. It must return a tuple (f(x), ∇f(x)) and,   if `g` is mutable, overwrite   it with the gradient.
  * `x0`: initial approximation

# Keywords

## Convergence criteria

There are two options to specify convergence criterion. The default is by `gtol` and the second by custom stop `convcond`.

  * `gtol::Real`: (default stop criterion) stop optimization when the gradient's 2-norm is less
  * `convcond=(x, xpre, y, ypre, g)->Bool`: function, custom stop criterion based on argument   values, function values and `g`radient. If `nothing` (default), corresponds to `gtol`,   and when specified, the `gtol`-criterion is ignored.

Example (default criterion): `convcond = (x, xpre, y, ypre, g) -> norm(g, 2) ≤ gtol`.

## Limitting optimization

(Un)Limit optimization process by specifing either `maxiter` and/or `maxcalls`.

  * `maxiter::Integer`: force stop optimization after this number of iterations   (use `nothing` or a negative value to not constrain iteration number)
  * `maxcalls::Integer`: force stop optimization after this number of function calls   (use `nothing` or a negative value to not constrain call number)

## Optimization constrains

The inequality constrains of optimization is handled by `constrain_step`.

  * `constrain_step(x0, d)`: a function to constrain step from `x0` in the direction `d`.   It must return a real-numbered value `α` such that `x0 + αd` is the maximum allowed step

## Initializing

  * `reset=true`: a value to pass as a keyword argument to the optimizer `init!` method

## Optimization path

  * `tracking::Union{Nothing,IO,AbstractString}`: IO stream or a file name to log the   optimization process or `nothing` to disable logging (default: `nothing`)
  * `verbosity::Integer`: verbosity of logging. `0` (default) disables tracking. `1` logs all   points of objective function evaluation with corresponding values and gradients.   `2` shows additional statistics regarding the line search. Option ignored if   `tracking == nothing`.
