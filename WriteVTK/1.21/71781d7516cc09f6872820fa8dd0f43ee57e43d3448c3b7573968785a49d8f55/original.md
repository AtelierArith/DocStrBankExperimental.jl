```
pvtk_grid(
    filename, args...;
    part, nparts, extents, ismain = (part == 1), ghost_level = 0,
    kwargs...,
)
```

Returns a handler representing a parallel VTK file, which can be eventually written to file with [`close`](@ref).

Positional and keyword arguments in `args` and `kwargs` are passed to [`vtk_grid`](@ref) verbatim. Note that serial filenames are automatically generated from `filename` and from the process id `part`.

The following keyword arguments only apply to parallel VTK file formats.

Mandatory ones are:

  * `part`: current (1-based) part id,
  * `nparts`: total number of parts (only required for **unstructured** grids),
  * `extents`: array specifying the partitioning of a **structured** grid across different processes (see below for details).

Optional ones are:

  * `ismain`: `true` if the current part id `part` is the main (the only one that will write the `.pvtk` file),
  * `ghost_level`: ghost level.

## Specifying extents for a structured grid

For structured grids, the partitioning of the dataset across different processes must be specified via the `extents` argument. This is an array where each element represents the data extent associated to a given process.

For example, for a dataset of global dimensions $15×12×4$ distributed across 4 processes, this array may look like the following:

```julia
extents = [
    ( 1:10,  1:5, 1:4),  # process 1
    (10:15,  1:5, 1:4),  # process 2
    ( 1:10, 5:12, 1:4),  # process 3
    (10:15, 5:12, 1:4),  # process 4
]
```

Some important notes:

  * the `extents` argument must be the same for all processes;
  * the extents **must overlap**, or VTK / ParaView will complain when trying to open the files;
  * the length of the `extents` array gives the number of processes. Therefore, the `nparts` argument is redundant and does not need to be passed.
