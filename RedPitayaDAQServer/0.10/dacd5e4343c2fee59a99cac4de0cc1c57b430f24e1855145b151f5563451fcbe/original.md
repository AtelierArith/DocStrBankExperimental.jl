```
@add_batch batch cmd
```

Append a usual RedPitaya function to the given batch instead of evaluating it directly.

See also [`ScpiBatch`](@ref), [`push!`](@ref), [`execute!`](@ref)

# Examples

```julia
julia>  execute!(rp) do b
          @add_batch b serverMode!(rp, CONFIGURATION)
        end
```
