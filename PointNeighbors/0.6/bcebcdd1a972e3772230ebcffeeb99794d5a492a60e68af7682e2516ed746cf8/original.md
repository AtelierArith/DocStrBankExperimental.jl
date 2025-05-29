```
GridNeighborhoodSearch{NDIMS}(; search_radius = 0.0, n_points = 0,
                              periodic_box = nothing,
                              cell_list = DictionaryCellList{NDIMS}(),
                              update_strategy = nothing)
```

Simple grid-based neighborhood search with uniform search radius. The domain is divided into a regular grid. For each (non-empty) grid cell, a list of points in this cell is stored. Instead of representing a finite domain by an array of cells, a potentially infinite domain is represented by storing cell lists in a hash table (using Julia's `Dict` data structure), indexed by the cell index tuple

$$
\left( \left\lfloor \frac{x}{d} \right\rfloor, \left\lfloor \frac{y}{d} \right\rfloor \right) \quad \text{or} \quad
\left( \left\lfloor \frac{x}{d} \right\rfloor, \left\lfloor \frac{y}{d} \right\rfloor, \left\lfloor \frac{z}{d} \right\rfloor \right),
$$

where $x, y, z$ are the space coordinates and $d$ is the search radius.

To find points within the search radius around a position, only points in the neighboring cells are considered.

See also (Chalela et al., 2021), (Ihmsen et al. 2011, Section 4.4).

As opposed to (Ihmsen et al. 2011), we do not sort the points in any way, since not sorting makes our implementation a lot faster (although less parallelizable).

# Arguments

  * `NDIMS`: Number of dimensions.

# Keywords

  * `search_radius = 0.0`:    The fixed search radius. The default of `0.0` is useful together                           with [`copy_neighborhood_search`](@ref).
  * `n_points = 0`:           Total number of points. The default of `0` is useful together                           with [`copy_neighborhood_search`](@ref).
  * `periodic_box = nothing`: In order to use a (rectangular) periodic domain, pass a                           [`PeriodicBox`](@ref).
  * `cell_list`:              The cell list that maps a cell index to a list of points inside                           the cell. By default, a [`DictionaryCellList`](@ref) is used.
  * `update_strategy = nothing`: Strategy to parallelize `update!`. Available options are:

      * `nothing`: Automatically choose the best available option.
      * [`ParallelUpdate()`](@ref): This is not available for all cell list implementations.
      * [`SemiParallelUpdate()`](@ref): This is available for all cell list implementations   and is the default when available.
      * [`SerialIncrementalUpdate()`](@ref)
      * [`SerialUpdate()`](@ref)

## References

  * M. Chalela, E. Sillero, L. Pereyra, M.A. Garcia, J.B. Cabral, M. Lares, M. Merchán. "GriSPy: A Python package for fixed-radius nearest neighbors search". In: Astronomy and Computing 34 (2021). [doi: 10.1016/j.ascom.2020.100443](https://doi.org/10.1016/j.ascom.2020.100443)
  * Markus Ihmsen, Nadir Akinci, Markus Becker, Matthias Teschner. "A Parallel SPH Implementation on Multi-Core CPUs". In: Computer Graphics Forum 30.1 (2011), pages 99–112. [doi: 10.1111/J.1467-8659.2010.01832.X](https://doi.org/10.1111/J.1467-8659.2010.01832.X)
