```julia
mutable struct Clock{T, CB}
```

`Clock` generates time instants to sample the systems. A `Clock` is an iterable 

# Fields

  * `generator::Any`: Internal generator. Can be any iterable
  * `paused::Bool`: If true, clock iteration is halted
  * `callbacks::Any`: Callback set. See [`Callback`](@ref)
  * `name::Symbol`: Name of clock
  * `uuid::Base.UUID`: Identiy number of clock

# Example

```jldoctest
julia> clk = Clock(0 : 2) 
Clock(gen:0:2, paused:false)

julia> for t in clk 
       @show t 
       end 
t = 0
t = 1
t = 2
```
