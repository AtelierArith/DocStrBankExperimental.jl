```
Piecewise(pairs... ; continuity = fill(-1, length(pairs) - 1))
```

A function defined by pieces (each associating a domain to a function). Support both intervals and standard numbers.

```jl
julia> myabs = Piecewise(
          Domain{:open, :closed}(-Inf, 0) => x -> -x,
          Domain{:open, :open}(0, Inf) => identity
       )
Piecewise function with 2 pieces:
  (-Inf, 0] -> var"#119#120"()
  (0, Inf) -> identity

julia> myabs(-22.3)
22.3

julia> myabs(interval(-5, 5))
Interval{Float64}(0.0, 5.0, def)
```

For constant pieces, it is recommended to use `Constant` for full compatibility with intervals.

The domains must be specified in increasing order and must not overlap.

The `continuity` optional argument takes a vector of `N - 1` integers (where  `N` is the number of domains) determining how the piecewise function behaves at the endpoints between the subdomains. The possibility are:

  * `-1` : the function is discontinuous between the domains.
  * `0` : the function is continuous but not differentiable between the domains.
  * `n > 0` : the function is `n` times continuously differentiable between the   domains. This only matter when using `ForwardDiff` to compute derivative   of the function.

This information is used to determine the decoration of intervals that covers the endpoint of several domains.

If an input interval goes outside the domain of definition of the piecewise function, the output will always have the trivial (`trv`) decoration. For standard number, it throws a `DomainError`.

The piecewise function can have a gap between two pieces. In this case, the `continuity` optional argument is ignored, and interval spanning over the gap always as the `trv` decoration.
