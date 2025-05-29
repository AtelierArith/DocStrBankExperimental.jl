```
@mpi_root expr
```

Evaluate expression only on the root rank. Extra care needs to be taken as `expr` *must not* contain any code that involves syncronising MPI operations, i.e. actions that would require syncronous action of all MPI ranks.

Example:

```julia
wn = walkernumber(dv)   # an MPI syncronising function call that gathers
                        # information from all MPI ranks
@mpi_root @info "The current walker number is" wn # print info message on root only
```
