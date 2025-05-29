```
ReportToFile(; kwargs...) <: ReportingStrategy
```

[`ReportingStrategy`](@ref) for [`ProjectorMonteCarloProblem`](@ref) that writes the report directly to a file in the [`Arrow`](https://arrow.apache.org/julia/dev/) format. Useful when dealing with long jobs or large numbers of replicas, when the report can incur a significant memory cost.

The arrow file can be read back in with [`load_df(filename)`](@ref) or `using Arrow; Arrow.Table(filename)`.

# Keyword arguments

  * `filename = "out.arrow"`: the file to report to. If the file already exists, a new file is created.
  * `reporting_interval = 1`: interval between simulation steps that are reported.
  * `chunk_size = 1000`: the size of each chunk that is written to the file. A `DataFrame` of this size is collected in memory and written to disk. When saving, an info message is also printed to `io`.
  * `save_if =`[`is_mpi_root()`](@ref Rimu.is_mpi_root): if this value is true, save the report, otherwise ignore it.
  * `return_df = false`: if this value is true, read the file and return the data frame at the end of computation. Otherwise, an empty `DataFrame` is returned.
  * `io = stdout`: The `IO` to print messages to. Set to `devnull` if you don't want to see messages printed out.
  * `compress = :zstd`: compression algorithm to use. Can be `:zstd`, `:lz4` or `nothing`.

See also [`load_df`](@ref), [`save_df`](@ref), [`ReportDFAndInfo`](@ref), and [`ProjectorMonteCarloProblem`](@ref).
