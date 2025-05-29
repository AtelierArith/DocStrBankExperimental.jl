```
@mpiroot [option] expression
```

Run the code if the mpi rank is zero. Lowers to something similar as:

```julia
if mpi_isroot()
    expression
end
```

# Options

  * `:wait`: All MPI ranks will wait until the root rank finishes evaluating `expression`.

See also: [`mpi_isroot`](@ref).
