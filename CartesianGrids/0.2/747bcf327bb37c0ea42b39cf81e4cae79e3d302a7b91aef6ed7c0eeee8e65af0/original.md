```
PhysicalGrid(xlim::Tuple{Real,Real},ylim::Tuple{Real,Real},Δx::Float64;[opt_type=:none,optimize_threads=false,nthreads_max=1])
```

Constructor to set up a grid connected to physical space. The region to be discretized by the grid is defined by the limits `xlim` and `ylim`, and the cell spacing (uniform and indentical in each direction) is specified by `Δx`. The constructor uses this information to determine the number of cells in each direction, expanding the given range if necessary to accommodate an integer number. It also pads each side with a ghost cell. It also determines the indices corresponding to the corner of the cell to which the physical origin corresponds. Note that the corner corresponding to the lowest limit in each direction has indices (1,1).

There are a few optional arguments devoted to optimization of the grid size. The `nthreads_max` sets the number of FFT compute threads to use and  can be set to a value up to the total number available on the architecture. It defaults to 1. 

The keyword `opt_type` can be set to `:threads`, `:prime` (default), or `:none`. If `:none`, then the grid is set as close to the specified range as possible. If `:prime`, then the grid is expanded in each direction to a number that is a product of primes (and therefore efficient in an FFT). If `:threads`, then the grid is tested with a representative calculation on various grid sizes to identify one that has the minimum cpu time. If `optimize_threads = true`, then the number of threads is also varied (between 1 and `nthreads_max`).
