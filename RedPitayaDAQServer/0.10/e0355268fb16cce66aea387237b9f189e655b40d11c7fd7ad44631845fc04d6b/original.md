```
execute!(f::Function, rp::Union{RedPitaya, RedPitayaCluster})
```

Open a `ScpiBatch` and evaluate the function `f`. If no exception was thrown, execute the opened batch.

See also [`ScpiBatch`](@ref), [`push!`](@ref), [`@add_batch`](@ref)

# Examples

```julia
julia>  execute!(rp) do b
          @add_batch b serverMode!(rp, CONFIGURATION)
          @add_batch b amplitudeDAC!(rp, 1, 1, 0.2)
        end
```
