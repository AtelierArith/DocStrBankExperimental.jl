```
NoOnset <: AbstractOnset
```

For cases where the user wants to simulate epoched data without any overlap between consecutive events.

# Examples

```julia-repl
julia> onset_distribution = NoOnset()
NoOnset()
```

See also [`UniformOnset`](@ref), [`LogNormalOnset`](@ref).
