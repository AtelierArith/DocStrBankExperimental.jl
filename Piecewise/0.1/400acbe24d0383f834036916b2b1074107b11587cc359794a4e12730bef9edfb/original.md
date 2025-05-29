```
piecewisefit(f::Function, domain::Tuple{Real, Real}, formulas::Vector{Formula}; kwargs...)
```

Return a piecewise approximation of the real-valued function `f(::Real)` in the domain `domain`, using the formulas given in the array `formulas` (see [`Formula`](@ref)).

## Optional keyword arguments

  * `parity` : Impose a parity (`:even` or `:odd`, default `:none`) to  the piecewise function
  * `singularities` : Points excluded from the domains (default `[]`)
  * `cuts` : Points forced to be piece boundaries (default `[]`)
  * `grain` : Minimal domain size, default `eps(Float64)`
  * `resolution` : Maximal distance between sampled points, default `Inf`
  * `rtol` : Relative tolerance, default `0.0`
  * `atol` : Absolute tolerance, default `eps(Float64)`
  * `loop` : Whether to return `f` in case of failure in a domain, default `false`

## Example

Here is a one-piece approximation to the function $\sin^{-1}(x)$. The power law at $x=1$ is represented exactly and a polynomial is fit to the rest:

```julia-repl
julia> f = PiecewiseFunction(:odd, Piece((0, 1), PLS, [1, 1 / 2, -sqrt(2)])) +
           piecewisefit(x -> asin(x) + sqrt(2 - 2 * x), (0, 1), [POLY],
           parity=:odd, atol=1e-5)
< Piecewise odd function with 1 piece and support [-1.0, 1.0] >

julia> max([abs(f(x) - asin(x)) for x in -1:0.1:1]...) < 1e-5
true
```
