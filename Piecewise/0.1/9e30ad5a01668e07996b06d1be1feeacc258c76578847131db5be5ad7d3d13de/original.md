```
Formula([name::String,] params::Integer, value::Function
    [, check::Function] [, scale::Function] [, mirror::Function])
```

Constructor of a `Formula` object with an optional name and a number of parameters that is exactly `params` if `params >= 0` and at most `-params` if `params < 0`. The value of the formula is set by the function `value(::Real, ::Vector{Any})`. The optional function `check(a::Vector{Any}, domain::Tuple{Real, Real}, included::Tuple{Bool, Bool}, danger::Bool, fatal::Bool)` must return `true` or `false` depending on whether the function `value(x, a)` is valid in the domain specified by `domain` and `included` (see [`Piece`](@ref)) with the parameters `a`. Warnings must be issued by `check` only if `danger` is `true` and errors must be thrown only if `fatal` is `true`. The optional function `scale(a::Vector{Any}, s::Number)` must return the parameters after multiplication of the formula by `s`. The optional function `mirror(a::Vector{Any})` must return the parameters after even reflection of the formula through $x=0$.

## Fields

  * `name::String`
  * `params::Integer`
  * `value::Function`
  * `check::Function`
  * `scale::Function`
  * `mirror::Function`

## Example

This creates a square-root singularity:

```julia-repl
julia> srs(x, a) = a[2] * sqrt(x - a[1])
julia> function srs(a, domain, included, danger, fatal)
           t = domain[1] > a[1] || (domain[1] == a[1] && ! included[1])
           !t && fatal && throw(ArgumentError("Singularity must be at left of domain."))
           t || return false
           t = a[2] >= 0
           !t && danger && @warn "Negative singularity in domain $(domain)."
           return true
       end
julia> F = Formula("SRS", 2, srs, srs)
Formula("SRS", 2, srs, srs)

julia> F.check([1, 1], (0, 2), (true, true), true, false)
false

julia> F.check([-1, -1], (0, 2), (true, true), true, false)
┌ Warning: Negative singularity in domain (0, 2).
└ @ Main REPL[3]:6
true
```
