```
ulam_method(traj, binner; reinj_algo)
```

Run the main Ulam's method calculation and return an [`UlamResult`](@ref).

This is the lower level method with all options available.

### Arguments

  * `traj`: A [`Trajectories`](@ref) object, holding the short-range trajectory data.
  * `binner`: A [`BinningAlgorithm`](@ref) that specifies the algorithm used to partition the boundary into bins.

### Optional Arguments

  * `reinj_algo`: A [`ReinjectionAlgorithm`](@ref) that specifies how trajectories pointing from nirvana to the interior should be reinjected. Default [`DataReinjection`](@ref).

---

```
ulam_method(traj, nbins; nirvana = 0.10)
```

Run the main Ulam's method calculation and return an [`UlamResult`](@ref).

This is the higher level "convenience" method with most options selected automatically.

### Nirvana Optional Argument

The boundary is placed such that a fraction `nirvana` of the data is in nirvana. For example, with the default  value of `0.10`, roughly `10%` of all of the datapoints (split between `x0` and `xT`) will be outside the boundary with  a roughly equal amount on each side.

The shape of the boundary can be further controlled by providing `nirvana` as a vector of length `Dim` of tuples of the form `(min, max)` such  that a fraction `min` (respectively `max`) will be "below" (respectively "above") the boundary along each dimension. 
