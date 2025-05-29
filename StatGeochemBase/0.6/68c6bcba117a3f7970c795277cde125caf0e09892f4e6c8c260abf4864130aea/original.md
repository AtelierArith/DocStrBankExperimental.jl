```julia
trapezoidalquadrature(edges, values)
```

Add up the area under a curve with y positions specified by a vector of `values` and x positions specfied by a vector of `edges` using trapezoidal integration. Bins need not be evenly spaced, though it helps (integration will be faster if `edges` are specified as an AbstractRange).

### Examples

```julia
julia> trapezoidalquadrature(0:0.1:10, 0:0.1:10)
50.0
```
