```
Stick(dpara::Float64, t2::Float64)
```

Return a Stick Type object with parallel diffusivity `dpara` and T2 relaxation time `t2`.  The perpendicular diffusivity of a Stick model is zero. 

# Examples

```julia-repl
julia> Stick(dpara = 1.7e-6, t2 = 60e-3)
Stick(1.7e-6, 0.06)
```
