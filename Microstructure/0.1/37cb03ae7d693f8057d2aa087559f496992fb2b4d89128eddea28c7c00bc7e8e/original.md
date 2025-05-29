```
Zeppelin(
    dpara::Float64, 
    dperp_frac::Float64, 
    t2::Float64
    )
```

Return a Zeppelin Type object with parallel diffusivity `dpara`, axially symmetric  perpendicular diffusivity represented as a fraction of the parallel diffusivity `dperp_frac`, and the T2 relaxation time `t2`.

# Examples

```julia-repl
julia> Zeppelin(dpara = 1.7e-6, dperp_frac = 0.5, t2 = 0.0)
Zeppelin(1.7e-6, 0.5, 0.0)
```
