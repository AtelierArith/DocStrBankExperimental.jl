```
allrays(vrep::VRep)
```

Returns an iterator over the rays and lines in the V-representation `vrep` splitting lines in two rays.

### Examples

```julia
vrep = Line([1, 0]) + Ray([0, 1])
collect(allrays(vrep)) # Returns [Ray([1, 0]), Ray([-1, 0]), Ray([0, 1])]
```
