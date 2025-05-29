```
show_construction([io::IO,] sys::LTISystem; name = "temp", letb = true)
```

Print code to `io` that reconstructs `sys`.

  * `letb`: If true, the code is surrounded by a let block.

```@example
julia> sys = ss(tf(1, [1, 1]))
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

julia> show_construction(sys, name="Jörgen")
Jörgen = let
    JörgenA = [-1.0;;]
    JörgenB = [1.0;;]
    JörgenC = [1.0;;]
    JörgenD = [0.0;;]
    ss(JörgenA, JörgenB, JörgenC, JörgenD)
end
```
