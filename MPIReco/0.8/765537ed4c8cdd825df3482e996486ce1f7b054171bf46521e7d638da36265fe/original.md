```
reconstruct(name::AbstractString, data::MPIFile, cache::Bool = false, modules = [AbstractImageReconstruction, MPIFiles, MPIReco, RegularizedLeastSquares]; kwargs...)
```

Perform a reconstruction with the `RecoPlan` specified by `name` and given `data`. Additional keyword arguments can be passed to the reconstruction plan.

`RecoPlans` can be stored in the in the MPIReco package config folder or in a custom folder. New folder can be added with `addRecoPlanPath`. The first plan found is used. Alternatively, name can be a path to specific plan file.

If `cache` is `true` the reconstruction plan is cached and reused if the plan file has not changed. If a keyword argument changes the structure of the plan the cache is also bypassed. The cache considers the last modification time of the plan file and can be manually be emptied with `emptyRecoCache!()`.

# Examples

```julia
julia> mdf = MPIFile("data.mdf");

julia> reconstruct("SinglePatch", mdf; solver = Kaczmarz, reg = [L2Regularization(0.3f0)], iterations = 10, frames = 1:10, ...)
```
