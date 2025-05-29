```
RectiGrid(dims::NamedTuple{Na}; executor=Serial(), header=ComradeBase.NoHeader(), posang=0.0)
RectiGrid(dims::NTuple{N, <:DimensionalData.Dimension}; executor=Serial(), header=ComradeBase.NoHeader(), posang=0.0)
```

Creates a rectilinear grid of pixels with the dimensions `dims`. The convention is that the first two dimension are the spatial dimensions `X/U` and `Y/V`. The remaining dimensions can be anything, for example:

  * (:X, :Y, :Ti, :Fr)
  * (:X, :Y, :Fr, :Ti)
  * (:X, :Y) # spatial only

where `X/U,Y/V` are the RA and DEC spatial dimensions in image/visibility space respectively,  `Ti` is the time dimension and `Fr` is the frequency dimension.

Note that the majority of the time users should just call [`imagepixels`](@ref) to create a spatial grid.

## Optional Arguments

  * `executor`: specifies how different models  are executed. The default is `Serial` which mean serial CPU computations. For threaded  computations use [`ThreadsEx()`](@ref) or load `OhMyThreads.jl` to uses their schedulers.
  * `header`: specified underlying header information for the grid. This is used to store  information about the image such as the source, RA and DEC, MJD.
  * `posang`: specifies the position angle of the grid, relative to RA=0 axis. Note that when            `posang != 0` the X and Y coordinate are relative to the rotated grid and not           the on sky RA and DEC orientation. To see the true on sky points you can access           them by calling `domainpoints(grid)`.

!!! warn
    The `posang` argument and the overall rotation of the grid is currently experimental and and may change abruptly in the future even on minor releases.


## Examples

```julia
dims = RectiGrid((X(-5.0:0.1:5.0), Y(-4.0:0.1:4.0), Ti([1.0, 1.5, 1.75]), Fr([230, 345])); executor=ThreadsEx())
dims = RectiGrid((X = -5.0:0.1:5.0, Y = -4.0:0.1:4.0, Ti = [1.0, 1.5, 1.75], Fr = [230, 345]); executor=ThreadsEx()))
```
