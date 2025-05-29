```
acqus(nmrdata)
acqus(nmrdata, key)
acqus(nmrdata, key, index)
```

Return data from a Bruker acqus file, or `nothing` if it does not exist. Keys can be passed as symbols or strings. If no key is specified, a dictionary is returned representing the entire acqus file.

If present, the contents of auxilliary files such as `vclist` and `vdlist` can be accessed using this function.

# Examples

```julia-repl
julia> acqus(expt, :pulprog)
"zgesgp"
julia> acqus(expt, "TE")
276.9988
julia> acqus(expt, :p, 1)
9.2
julia> acqus(expt, "D", 1)
0.1
julia> acqus(expt, :vclist)
11-element Vector{Int64}:
[...]
```

See also [`metadata`](@ref).
