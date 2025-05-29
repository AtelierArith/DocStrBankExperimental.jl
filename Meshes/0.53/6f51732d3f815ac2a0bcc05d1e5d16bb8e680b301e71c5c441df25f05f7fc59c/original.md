```
RegularGrid(dims, origin, spacing)
```

A regular grid with dimensions `dims`, lower left corner at `origin` and cell spacing `spacing`. The three arguments must have the same length.

```
RegularGrid(dims, origin, spacing, offset)
```

A regular grid with dimensions `dims`, with lower left corner of element `offset` at `origin` and cell spacing `spacing`.

```
RegularGrid(start, finish, dims=dims)
```

Alternatively, construct a regular grid from a `start` point to a `finish` with dimensions `dims`.

```
RegularGrid(start, finish, spacing)
```

Alternatively, construct a regular grid from a `start` point to a `finish` point using a given `spacing`.

```
RegularGrid(dims)
RegularGrid(dim1, dim2, ...)
```

Finally, a regular grid can be constructed by only passing the dimensions `dims` as a tuple, or by passing each dimension `dim1`, `dim2`, ... separately. In this case, the origin and spacing default to (0,0,...) and (1,1,...).

## Examples

Create a 3D grid with 100x100x50 hexahedrons:

```julia
julia> RegularGrid(100, 100, 50)
```

Create a 2D grid with 100 x 100 quadrangles and origin at (10.0, 20.0):

```julia
julia> RegularGrid((100, 100), (10.0, 20.0), (1.0, 1.0))
```

Create a 1D grid from -1 to 1 with 100 segments:

```julia
julia> RegularGrid((-1.0,), (1.0,), dims=(100,))
```

See also [`CartesianGrid`](@ref).
