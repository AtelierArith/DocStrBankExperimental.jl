```julia
midpointquadrature(bincenters, values)
```

Add up the area under a curve with y positions specified by a vector of `values` and x positions specfied by a vector of `bincenters` using midpoint integration.

### Examples

```julia
julia> midpointquadrature(0:0.1:10, 0:0.1:10)
50.5
```
