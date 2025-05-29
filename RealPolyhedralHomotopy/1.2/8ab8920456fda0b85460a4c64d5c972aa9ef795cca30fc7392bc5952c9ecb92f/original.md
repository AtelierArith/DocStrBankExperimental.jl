```
generate_binomials(F::System)
```

Return a wrapper object Binomial*system*data from an input polynomial system. Binomial systems obtained from the mixed cells induced by the $Log|C|$-lifting. The object Binomial*system*data contains the binomial system, normal vectors, lifting vectors, and cells from the mixed subdivision computed. The object Binomial*system*data is used as an input for the rph_track function.

# Arguments

  * `F` : The target system for the real polyhedral homotopy.

```julia
B = generate_binomials(F)
```

```
Binomial_system_data
```

```julia
B.binomial_system
```

```
2-element Vector{Any}:
 Expression[-24000*y + x^3, 50*x*y - y^2]
 Expression[-24000*y + x^3, -9 + 50*x*y]
```
