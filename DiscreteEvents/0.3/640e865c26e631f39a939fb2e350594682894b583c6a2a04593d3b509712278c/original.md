```
tau(clk::Clock=𝐶)
```

Return the current simulation time.

# Examples

```jldoctest
julia> using DiscreteEvents

julia> resetClock!(𝐶)   # reset the default clock
"clock reset to t₀=0.0, sampling rate Δt=0.01."
julia> tau()            # gives the default clock's time
0.0
```
