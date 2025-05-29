```
taylorinteg(f, g, x0, t0, tmax, order, abstol, params[=nothing]; kwargs... )
taylorinteg(f, g, x0, t0, tmax, order, abstol, params[=nothing]; kwargs... )
taylorinteg(f, g, x0, t0, tmax, order, abstol, params[=nothing]; kwargs... )
taylorinteg(f, g, x0, trange, order, abstol, params[=nothing]; kwargs... )
```

Root-finding method of `taylorinteg`.

Given a function `g(dx, x, params, t)::Tuple{Bool, Taylor1{T}}`, called the event function, `taylorinteg` checks for the occurrence of a root or event defined by `cond2 == 0` (`cond2::Taylor1{T}`) if `cond1::Bool` is satisfied (`true`); `g` is thus assumed to return the tuple (cond1, cond2). Then, `taylorinteg` attempts to find that root (or event, or crossing) by performing a Newton-Raphson process. When called with the `eventorder=n` keyword argument, `taylorinteg` searches for the roots of the `n`-th derivative of `cond2`, which is computed via automatic differentiation.

The current keyword argument are:

  * `maxsteps[=500]`: maximum number of integration steps.
  * `parse_eqs[=true]`: use the specialized method of `jetcoeffs!` created   with [`@taylorize`](@ref).
  * `eventorder[=0]`: order of the derivative of `g` whose roots are computed.
  * `newtoniter[=10]`: maximum Newton-Raphson iterations per detected root.
  * `nrabstol[=eps(T)]`: allowed tolerance for the Newton-Raphson process; T is the common   type of `t0`, `tmax` (or `eltype(trange)`) and `abstol`.
  * `dense[=true]`: output the Taylor polynomial expansion at each time step.

## Examples:

```julia
using TaylorIntegration

function pendulum!(dx, x, params, t)
    dx[1] = x[2]
    dx[2] = -sin(x[1])
    nothing
end

g(dx, x, params, t) = (true, x[2])

x0 = [1.3, 0.0]

# find the roots of `g` along the solution
sol = taylorinteg(pendulum!, g, x0, 0.0, 22.0, 28, 1.0E-20)

# find the roots of the 2nd derivative of `g` along the solution
sol = taylorinteg(pendulum!, g, x0, 0.0, 22.0, 28, 1.0E-20; eventorder=2)

# find the roots of `g` along the solution, with dense solution output
sol = taylorinteg(pendulum!, g, x0, 0.0, 22.0, 28, 1.0E-20, dense=true)

# times at which the solution will be returned
tv = 0.0:1.0:22.0

# find the roots of `g` along the solution; return the solution *only* at each value of `tv`
sol = taylorinteg(pendulum!, g, x0, tv, 28, 1.0E-20)

# find the roots of the 2nd derivative of `g` along the solution; return the solution *only* at each value of `tv`
sol = taylorinteg(pendulum!, g, x0, tv, 28, 1.0E-20; eventorder=2)
```
