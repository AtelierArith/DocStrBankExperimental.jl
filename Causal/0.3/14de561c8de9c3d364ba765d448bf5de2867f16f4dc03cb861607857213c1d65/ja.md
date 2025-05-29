```julia
pause!(clk)

```

`clk`を一時停止します。一時停止中は、時計の反復が停止します。

# 例

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
