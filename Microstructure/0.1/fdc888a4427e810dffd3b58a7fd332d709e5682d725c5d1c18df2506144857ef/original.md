```
Iso(diff::Float64, t2=Float64)
```

Return an isotropic tensor with diffusivity `diff` and T2 relaxation time `t2`.  This compartment can be used to represent CSF (`diff` = free water) or dot compartment (`diff` = 0).  The latter is for immobile water typically seen in ex vivo tissue.  This compartment can also represent an isotropic extra-cellular environment with diffusivity `diff` slower than free water.

# Examples

```julia-repl
julia> Iso(diff = 3.0e-9,t2 = 2000.0e-3)
Iso(3.0e-9, 2.0)
```

```julia-repl
julia> Iso(diff = 0.0)
Iso(0.0, 0.0)
```
