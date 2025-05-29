```julia
pause!(clk)

```

Pauses `clk`. When paused, the iteration of clock is halted. 

# Example

```jldoctest
julia> clk = Clock(0 : 5)
Clock(gen:0:5, paused:false)

julia> iterate(clk) 
(0, 0)

julia> iterate(clk, 1)
(2, 2)

julia> pause!(clk) 
Clock(gen:0:5, paused:true)

julia> iterate(clk, 1)
┌ Warning: Clock is paused
└ @ Causal ~/.julia/dev/Causal/src/components/sources/clock.jl:41
```
