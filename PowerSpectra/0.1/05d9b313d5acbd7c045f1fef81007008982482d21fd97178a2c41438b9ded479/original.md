```
function fitdipole(m::HealpixMap{T}, [w::HealpixMap{T}=1]) where T
```

Fit the monopole and dipole of a map. 

# Arguments:

  * `m::HealpixMap{T}`: map to fit
  * `w::HealpixMap{T}`: weight map. Defaults to a FillArray of ones.

# Returns:

  * `Tuple{T, NTuple{3,T}}`: (monopole, (dipole x, dipole y, dipole z))
