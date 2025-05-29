```
ncread(file, var [, selection]; kwargs...) → A
```

Load the variable `var` from the `file` and convert it into a [`ClimArray`](@ref) with proper dimension mapping and also containing the variable attributes as a dictionary. Dimension attributes are also given to the dimensions of `A`, if any exist. See keywords below for specifications for unstructured grids.

`file` can be a string to a `.nc` file. Or, it can be an `NCDataset`, which allows you to lazily combine different `.nc` data (typically split by time), e.g.

```julia
using Glob # for getting all files
alldata = glob("toa_fluxes_*.nc")
file = NCDataset(alldata; aggdim = "time")
A = ClimArray(file, "tow_sw_all")
```

`var` is a `String` denoting which variable to load. For `.nc` data containing groups `var` can also be a tuple `("group_name", "var_name")` that loads a specific variable from a specific group. In this case, the attributes of both the group and the CF-variable are attributed to the created [`ClimArray`](@ref).

Optionally you can provide a `selection` for selecting a smaller part of the full array. The `selection` must be a tuple of indices that compose the selection and you must specify exactly as many ranges as the dimensions of the array and in the correct order. For example, if `var` corresponds to an array with three dimensions, such syntaxes are possible:

```julia
(:, :, 1:3)
(1:5:100, 1:1, [1,5,6])
```

The function [`ncsize`](@ref) can be useful for `selection`.

See also [`ncdetails`](@ref), [`nckeys`](@ref) and [`ncwrite`](@ref).

## Smart loading

The following things make loading data with `ncread` smarter than directly trying to use NCDatasets.jl and then convert to some kind of dimensional container.

1. Data are directly transformed into `ClimArray`, conserving metadata and dimension names.
2. If there are no missing values in the data (according to CF standards), the returned array is automatically converted to a concrete type (i.e. `Union{Float32, Missing}` becomes `Float32`).
3. Dimensions that are ranges (i.e. sampled with constant step size) are automatically transformed to a standard Julia `Range` type (which makes sub-selecting faster).
4. Automatically deducing whether the spatial information is in an orthogonal grid or not, and creating a single `Coord` dimension if not.

## Keywords

  * `name` optionally rename loaded array.
  * `grid = nothing` optionally specify whether the underlying grid is `grid = OrthogonalSpace()` or `grid = CoordinateSpace()`, see [Types of spatial information](@ref). If `nothing`, we try to deduce automatically based on the names of dimensions and other keys of the `NCDataset`.
  * `lon, lat`. These two keywords are useful in unstructured grid data where the grid information is provided in a *separate .nc file*. What we need is the user to provide vectors of the central longitude and central latitude of each grid point. This is done e.g. by

    ```julia
    ds = NCDataset("path/to/grid.nc");
    lon = Array(ds["clon"]);
    lat = Array(ds["clat"]);
    ```

    If `lon, lat` are given, `grid` is automatically assumed `CoordinateSpace()`.
  * `celldim = nothing`: only used for `CoordinateSpace`: when `
