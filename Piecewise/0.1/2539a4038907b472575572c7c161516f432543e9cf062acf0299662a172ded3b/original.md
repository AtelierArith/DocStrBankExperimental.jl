```
Piece(domain, [included,] rule, parameters)
```

Constructor of a `Piece` object in the domain defined by the argument `domain::Tuple{Real, Real}`. The argument `included::Tuple{Bool, Bool}`, by default `(true, true)`, tells whether the domain boundaries belong to the domain. The arguments `rule::Vector{Formula}` and `parameters::Vector{Vector{Any}}` specify the rule used to evaluate the value of the piece (see [`Formula`](@ref)). It is also possible to pass `rule::Formula` and `parameters::Vector{Any}` for a single formula.

```
Piece(domain, [included,] function)
```

Initialization with a single function. This is equivalent to `Piece(domain, [included,] Formula(0, (x, a)->function(x)), Any[])`.

## Fields

  * `domain::Tuple{Real, Real}`
  * `included::Tuple{Bool, Bool}`
  * `rule::Vector{Formula}`
  * `parameters::Vector{Vector{Any}}`

## Examples

This represents $1/x$ for strictly positive numbers:

```julia-repl
julia> Piece((0, Inf), (false, true), x -> 1 / x)
< Piece of type unnamed over the domain ]0.0, Inf] >

```

This represents $-\log|x|$ for $x\in ]0, 1]$:

```julia-repl
julia> Piece((0, 1), (false, true), Formula("LOG", 1, (x, a) -> a[1] * log(abs(x))), [-1])
< Piece of type LOG over the domain ]0.0, 1.0] >

```
