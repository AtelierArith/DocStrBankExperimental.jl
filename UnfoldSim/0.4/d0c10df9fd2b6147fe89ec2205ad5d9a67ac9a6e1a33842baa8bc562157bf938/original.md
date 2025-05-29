```
orientation(hart::Hartmut; type = "cortical")
```

Return the orientations of the (cortical or artefacual) sources of the HArtMuT model. 

The norm of the orientation vectors is 1 and the values are between -1 and 1.

# Keyword arguments

  * `type = "cortical"`: Defines whether the "cortical" or "artefactual" orientations should be returned.

# Returns

  * `Matrix{Float64}`: Orientations in 3D space. The output dimensions are `sources x spatial dimensions`.

# Examples

```julia-repl
julia> h = Hartmut();
Please cite: HArtMuT: Harmening Nils, Klug Marius, Gramann Klaus and Miklody Daniel - 10.1088/1741-2552/aca8ce

julia> orientation(h)
2004×3 Matrix{Float64}:
 -0.921919   0.364292   0.131744
 -0.900757  -0.415843  -0.125345
 -0.954087   0.117479  -0.27553
 -0.814613  -0.55344    0.17352
 -0.790526   0.276849  -0.546281
  ⋮                    
 -0.962905   0.20498   -0.17549
 -0.828358   0.557468  -0.0552498
 -0.963785  -0.265607  -0.0239074
 -0.953909   0.203615   0.22045
 -0.75762    0.128027   0.640016
```
