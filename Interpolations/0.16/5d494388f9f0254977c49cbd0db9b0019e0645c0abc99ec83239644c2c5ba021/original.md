```
knots(itp::AbstractInterpolation)
knots(etp::AbstractExtrapolation)
```

Returns an iterator over knot locations for an AbstractInterpolation or AbstractExtrapolation.

Iterator will yield scalar values for interpolations over a single dimension, and tuples of coordinates for higher dimension interpolations. Iteration over higher dimensions is taken as the product of knots along each dimension.

i.e., Iterator.product(knots on 1st dim, knots on 2nd dim,...)

Extrapolations with Periodic or Reflect boundary conditions, will produce an infinite sequence of knots.

# Example

```jldoctest
julia> etp = linear_interpolation([1.0, 1.2, 2.3, 3.0], rand(4); extrapolation_bc=Periodic());

julia> Iterators.take(knots(etp), 5) |> collect
5-element Vector{Float64}:
 1.0
 1.2
 2.3
 3.0
 3.2
```
