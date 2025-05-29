```
Calculation{P<:Package}(name    ::String;
                        flags   ::AbstractDict = Dict{Symbol, Any}(),
                        data    ::Vector{InputData} = InputData[],
                        exec    ::Exec,
                        run     ::Bool = true,
                        infile  ::String = P == Wannier90 ? name * ".win" : name * ".in",
                        outfile ::String = name * ".out")
```

The representation of a *DFT* calculation of package `P`, holding the `flags` that will be written to the `infile`, the executable `exec` and the output written by the calculation to the `outfile`. It essentially represents a line in a job script similar to `exec < infile.in > outfile.out`.  `outdata` stores the parsed calculation output after it was read at least once. The `run` field indicates whether the calculation should be actually performed, e.g. if `run=false` the corresponding line will be commented out in the job script.

```
Calculation{P<:Package}(name::AbstractString, flags::Pair{Symbol, Any}...; kwargs...)
```

Create a [`Calculation`](@ref) from `name` and `flags`, other `kwargs...` will be passed to the constructor.

```
Calculation(template::Calculation, name::AbstractString, flags::Pair{Symbol, Any}...; excs=deepcopy(template.exec), run=true, data=nothing)
```

Creates a new [`Calculation`](@ref) from the `template`, setting the `flags` of the newly created one to the specified ones.
