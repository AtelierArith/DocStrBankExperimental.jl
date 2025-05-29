```
ReportDFAndInfo(; reporting_interval=1, info_interval=100, io=stdout, writeinfo=false) <: ReportingStrategy
```

The default [`ReportingStrategy`](@ref) for [`ProjectorMonteCarloProblem`](@ref). Report every `reporting_interval`th step to a `DataFrame` and write info message to `io` every `info_interval`th reported step (unless `writeinfo == false`). The flag `writeinfo` is useful for controlling info messages in MPI codes, e.g. by setting `writeinfo =`[`is_mpi_root()`](@ref Rimu.is_mpi_root).

See also [`ProjectorMonteCarloProblem`](@ref), [`ReportToFile`](@ref).
