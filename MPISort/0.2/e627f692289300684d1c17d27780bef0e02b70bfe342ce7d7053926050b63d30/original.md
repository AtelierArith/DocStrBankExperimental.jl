```julia
struct SIHSort <: Base.Sort.Algorithm
```

Sampling with interpolated histograms sorting algorithm, or SIHSort (pronounce *sigh* sort).

# Methods

```
SIHSort(comm)
SIHSort(comm, sorter)
SIHSort(;comm=MPI.COMM_WORLD, sorter=nothing, stats=SIHSortStats())
```

# Fields

  * `comm::MPI.Comm`: MPI communicator used. Default: MPI.COMM_WORLD
  * `root::Int64`: MPI root rank for reductions. Default: 0
  * `sorter::Union{Nothing, Function, Base.Sort.Algorithm}`: Local in-place sorter used. Default: nothing
  * `stats::MPISort.SIHSortStats`: Useful stats saved after sorting, e.g. elements' partitioning. Default: SIHSortStats()
