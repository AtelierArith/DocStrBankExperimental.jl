Linear interpolation in one dimension

##### Fields

  * `breaks::AbstractVector` : A sorted array of grid points on which to interpolate
  * `vals::AbstractVector` : The function values associated with each of the grid points

##### Examples

```julia
breaks = cumsum(0.1 .* rand(20))
vals = 0.1 .* sin.(breaks)
li = LinInterp(breaks, vals)

# do interpolation via `call` method on a LinInterp object
li(0.2)

# use broadcasting to evaluate at multiple points
li.([0.1, 0.2, 0.3])
```
