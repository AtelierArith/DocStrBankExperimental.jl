```
Domain(; kwargs...)
```

Describes the optimization domain.

# Keywords

  * `bounds::AbstractBounds`: The basic box-constraints on `x`. This field is mandatory.
  * `discrete::AbstractVector{<:Bool}`: Can be used to designate some dimensions       of the domain as discrete.
  * `cons::Union{Nothing, Function}`: Used to define arbitrary nonlinear constraints on `x`.       Feasible points `x` must satisfy `all(cons(x) .> 0.)`. An appropriate acquisition       maximizer which can handle nonlinear constraints must be used if `cons` is provided.       (See [`AcquisitionMaximizer`](@ref).)
