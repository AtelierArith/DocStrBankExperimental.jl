```julia
setup_mpi(; args...)

```

Look first at the list of clusters that have "presets" available,  by typing `Pigeons.setup_mpi_` and then tab. These are the most  straightforward to use. 

If presets are not available, use `setup_mpi()`. To see the  documentation of the arguments of `setup_mpi()`, see  [`MPISettings`](@ref) (i.e. `args...` are passed to the constructor of [`MPISettings`](@ref)). 

Pull requests to `Pigeons/src/submission/presets.jl` are welcome  if you would like to add a new "preset" functions of the form  `Pigeons.setup_mpi_...()`.
