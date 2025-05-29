```julia
struct Sample <: Symbolics.Operator
```

Represents a sample operator. A discrete-time signal is created by sampling a continuous-time signal.

# Constructors

`Sample(clock::TimeDomain = InferredDiscrete())` `Sample([t], dt::Real)`

`Sample(x::Num)`, with a single argument, is shorthand for `Sample()(x)`.

# Fields

  * `clock`

# Examples

```jldoctest
julia> using Symbolics

julia> @variables t;

julia> Δ = Sample(t, 0.01)
(::Sample) (generic function with 2 methods)
```
