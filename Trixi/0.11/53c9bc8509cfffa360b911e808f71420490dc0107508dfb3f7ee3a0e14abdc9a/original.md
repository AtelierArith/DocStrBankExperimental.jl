```
TimeSeriesCallback(semi, point_coordinates;
                   interval=1, solution_variables=cons2cons,
                   output_directory="out", filename="time_series.h5",
                   RealT=real(solver), uEltype=eltype(cache.elements))
```

Create a callback that records point-wise data at points given in `point_coordinates` every `interval` time steps. The point coordinates are to be specified either as a vector of coordinate tuples or as a two-dimensional array where the first dimension is the point number and the second dimension is the coordinate dimension. By default, the conservative variables are recorded, but this can be controlled by passing a different conversion function to `solution_variables`.

After the last time step, the results are stored in an HDF5 file `filename` in directory `output_directory`.

The real data type `RealT` and data type for solution variables `uEltype` default to the respective types used in the solver and the cache.

Currently this callback is only implemented for [`TreeMesh`](@ref) and [`UnstructuredMesh2D`](@ref).
