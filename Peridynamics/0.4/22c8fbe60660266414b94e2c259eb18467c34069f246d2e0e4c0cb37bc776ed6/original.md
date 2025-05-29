```
@mpitime expression
```

Time the `expression` if the mpi rank is zero. Lowers to:

```julia
if mpi_isroot()
    @time expression
else
    expression
end
```

See also: [`mpi_isroot`](@ref).
