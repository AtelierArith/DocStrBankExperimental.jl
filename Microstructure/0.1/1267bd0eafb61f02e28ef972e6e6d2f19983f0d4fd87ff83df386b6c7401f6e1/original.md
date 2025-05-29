```
Cylinder(
    da::Float64, 
    dpara::Float64, 
    d0::Float64, 
    t2::Float64
    )
```

Return a Cylinder Type object with the cylinder diameter `da`, parallel diffusivity `dpara`,  the intrinsic diffusivity `d0` and the T2 relaxation time `t2`. 

# Examples

```julia-repl
julia> Cylinder(da = 3.0e-6, dpara = 1.8e-9, d0 = 1.7e-9, t2 = 90e-3)
Cylinder(3.0e-6, 1.8e-9, 1.7e-9, 0.09)
```
