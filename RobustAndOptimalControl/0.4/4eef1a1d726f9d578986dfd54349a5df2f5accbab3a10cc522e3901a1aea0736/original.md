```
vec2sys(v::AbstractArray, ny::Int, nu::Int, ts = nothing)
```

Create a statespace system from the parameters

```julia
v = vec(sys) = [vec(sys.A); vec(sys.B); vec(sys.C); vec(sys.D)]
```

Use `vec(sys)` to create `v`.

This can be useful in order to convert to and from vectors for, e.g., optimization.

```@example
julia> sys  = ss(tf(1, [1, 1]))
StateSpace{Continuous, Float64}
A = 
 -1.0
B = 
 1.0
C = 
 1.0
D = 
 0.0

Continuous-time state-space model

julia> v    = vec(sys)
4-element Vector{Float64}:
 -1.0
  1.0
  1.0
  0.0

julia> sys2 = vec2sys(v, sys.ny, sys.nu)
StateSpace{Continuous, Float64}
A = 
 -1.0
B = 
 1.0
C = 
 1.0
D = 
 0.0

Continuous-time state-space model
```
