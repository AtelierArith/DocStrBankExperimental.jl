```
iqsim(trainimg::AbstractArray{T,N}, tilesize::Dims{N},
      simsize::Dims{N}=size(trainimg);
      overlap::NTuple{N,<:Real}=ntuple(i->1/6,N),
      soft::AbstractVector=[], hard::Dict=Dict(), tol::Real=.1,
      path::Symbol=:raster, nreal::Integer=1,
      debug::Bool=false, showprogress::Bool=true,
      rng::AbstractRNG=Random.default_rng())
```

Performs image quilting simulation as described in Hoffimann et al. 2017.

## Parameters

### Required

  * `trainimg` is any Julia array
  * `tilesize` is the tile size

### Optional

  * `simsize` is the size of the simulation grid (default to training image size)
  * `overlap` is the percentage of overlap (default to 1/6 of tile size)
  * `soft` is a vector of `(data,dataTI)` pairs (default to none)
  * `hard` is a dictionary mapping coordinates to data values (default to none)
  * `tol` is the initial relaxation tolerance in (0,1] (default to .1)
  * `path` is the simulation path (`:raster`, `:dilation` or `:random`)
  * `nreal` is the number of realizations (default to 1)
  * `debug` informs whether to export or not the boundary cuts and voxel reuse
  * `showprogress` informs whether to show or not estimated time duration
  * `rng` is the random number generator (default to `Random.default_rng()`)

The main output `reals` consists of a list of realizations that can be indexed with `reals[1], reals[2], ..., reals[nreal]`. If `debug=true`, additional output is generated:

```julia
reals, cuts, voxs = iqsim(..., debug=true)
```

`cuts[i]` is the boundary cut for `reals[i]` and `voxs[i]` is the associated voxel reuse.
