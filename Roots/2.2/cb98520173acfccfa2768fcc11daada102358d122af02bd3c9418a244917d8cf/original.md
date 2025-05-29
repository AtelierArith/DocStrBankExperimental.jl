```
solve!(P::ZeroProblemIterator)
solve(fx::ZeroProblem, [M], [N]; p=nothing, kwargs...)
init(fx::ZeroProblem, [M], [N];
     p=nothing,
     verbose=false, tracks=NullTracks(), kwargs...)
```

Solve for the zero of a scalar-valued univariate function specified through `ZeroProblem` or `ZeroProblemIterator` using the `CommonSolve` interface.

The defaults for `M` and `N` depend on the `ZeroProblem`: if `x0` is a number, then `M=Secant()` and `N=AlefeldPotraShi()` is used (`Order0`); if `x0` has `2` (or more values) then it is assumed to be a bracketing interval and `M=AlefeldPotraShi()` is used.

The methods involved with this interface are:

  * `ZeroProblem`: used to specify a problem with a function (or functions) and an initial guess
  * `solve`: to solve for a zero in a `ZeroProblem`

The latter calls the following, which can be useful independently:

  * `init`: to initialize an iterator with a method for solution, any adjustments to the default tolerances, and a specification to log the steps or not.
  * `solve!` to iterate to convergence.

Returns `NaN`, not an error like `find_zero`, when the problem can not be solved. Tested for zero allocations.

## Examples:

```jldoctest find_zero
julia> using Roots

julia> fx = ZeroProblem(sin, 3)
ZeroProblem{typeof(sin), Int64}(sin, 3)

julia> solve(fx)
3.141592653589793
```

Or, if the iterable is required

```jldoctest find_zero
julia> problem = init(fx);

julia> solve!(problem)
3.141592653589793
```

keyword arguments can be used to adjust the default tolerances.

```jldoctest find_zero
julia> solve(fx, Order5(); atol=1/100)
3.1425464815525403
```

The above is equivalent to:

```jldoctest find_zero
julia> problem = init(fx, Order5(), atol=1/100);

julia> solve!(problem)
3.1425464815525403
```

The keyword argument `p` may be used if the function(s) to be solved depend on a parameter in their second positional argument (e.g., `f(x, p)`). For example

```jldoctest find_zero
julia> f(x,p) = exp(-x) - p # to solve p = exp(-x)
f (generic function with 1 method)

julia> fx = ZeroProblem(f, 1)
ZeroProblem{typeof(f), Int64}(f, 1)

julia> solve(fx; p=1/2)  # log(2)
0.6931471805599453
```

This would be recommended, as there is no recompilation due to the function changing. For use with broadcasting, `p` may also be the last positional argument.

The argument `verbose=true` for `init` instructs that steps to be logged;

The iterator interface allows for the creation of hybrid solutions, such as is used when two methods are passed to `solve`. For example, this is essentially how the hybrid default is constructed:

```jldoctest find_zero
julia> function order0(f, x)
           fx = ZeroProblem(f, x)
           p = init(fx, Roots.Secant())
           xᵢ,st = ϕ = iterate(p)
           while ϕ !== nothing
               xᵢ, st = ϕ
               state, ctr = st
               fᵢ₋₁, fᵢ = state.fxn0, state.fxn1
               if sign(fᵢ₋₁)*sign(fᵢ) < 0 # check for bracket
                   x0 = (state.xn0, state.xn1)
                   fx′ = ZeroProblem(f, x0)
                   p = init(fx′, Bisection())
                   xᵢ = solve!(p)
                   break
               end
               ϕ = iterate(p, st)
           end
           xᵢ
       end
order0 (generic function with 1 method)

julia> order0(sin, 3)
3.141592653589793
```
