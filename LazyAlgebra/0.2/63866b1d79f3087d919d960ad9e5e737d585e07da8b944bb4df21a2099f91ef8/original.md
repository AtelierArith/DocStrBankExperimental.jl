# Linear conjugate gradient

```julia
conjgrad!(x, A, b, [x0=vfill!(x,0), p, q, r]) -> x
```

finds an approximate solution to the symmetric linear system `A⋅x = b` starting at `x0` by means of the iterative conjugate gradient method.  The result is stored in `x` which is returned.

Argument `A` implements the symmetric positive definite linear mapping `A`, it can be provided as a Julia array (interpreted as a general matrix, see [`GeneralMatrix`](@ref)), as an instance of [`LinearMapping`](@ref) or as a callable object (like a function) which is used as:

```julia
A(dst, src)
```

to overwrite `dst` with `A⋅src`.  If `A` has been implemented as a callable object, such that `A(x)` yields `A⋅x`, then call `conjgrad!` with an inline function:

```julia
conjgrad!(x, (dst,src) -> (dst .= A(src); return dst), b, ...)
```

If no initial variables are specified, the default is to start with all variables set to zero.

Optional arguments `p`, `q` and `r` are writable workspace *vectors*.  On return, `p` is the last search direction, `q = A⋅p` and `r = b - A⋅xp` with `xp` the previous or last solution.  If provided, these workspaces must be distinct.  All *vectors* must have the same sizes.  If all workspace vectors are provided, no other memory allocation is necessary (unless `A` needs to allocate some temporaries).

Provided `A` be positive definite, the solution `x` of the equations `A⋅x = b` is also the minimum of the quadratic function:

```
f(x) = (1/2) x'⋅A⋅x - b'⋅x + ϵ
```

where `ϵ` is an arbitrary constant.  The variations of `f(x)` between successive iterations, the norm of the gradient of `f(x)` or the variations of `x` may be used to decide the convergence of the algorithm (see keywords `ftol`, `gtol` and `xtol` below).

## Saving memory

To save memory, `x` and `x0` can be the same object.  Otherwise, if no restarting occurs (see keyword `restart` below), `b` can also be the same as `r` but this is not recommended.

## Keywords

There are several keywords to control the algorithm:

  * Keyword `ftol` specifies the function tolerance for convergence.  The convergence is assumed as soon as the variation of the objective function `f(x)` between two successive iterations is less or equal `ftol` times the largest variation so far.  By default, `ftol = 1e-8`.
  * Keyword `gtol` specifies the gradient tolerances for convergence, it is a tuple of two values `(gatol, grtol)` which are the absolute and relative tolerances.  Convergence occurs when the Euclidean norm of the residuals (which is that of the gradient of the associated objective function) is less or equal the largest of `gatol` and `grtol` times the Euclidean norm of the initial residuals.  By default, `gtol = (0.0, 0.0)`.
  * Keyword `xtol` specifies the variables tolerance for convergence.  The convergence is assumed as soon as the Euclidean norm of the change of variables is less or equal `xtol` times the Euclidean norm of the variables `x`.  By default, `xtol = 0`.
  * Keyword `maxiter` specifies the maximum number of iterations which is practically unlimited by default.
  * Keyword `restart` may be set with the maximum number of iterations before restarting the algorithm.  By default, `restart` is set with the smallest of `50` and the number of variables.  Set `restart` to at least `maxiter` if you do not want that any restarts ever occur.
  * Keyword `strict` can be set to a boolean value (default is `true`) to specify whether non-positive definite operator `A` throws a `NonPositiveDefinite` exception or just returns the best solution found so far (with a warning if `quiet` is false).
  * Keyword `quiet` can be set to a boolean value (default is `false`) to specify whether or not to print warning messages.

See also: [`conjgrad`][@ref).
