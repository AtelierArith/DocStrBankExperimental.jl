```
fotf2cotf(tf)
```

Convert an FOTF object to a commensurate order object.

### Example

```julia-repl
julia> fotf2cotf(G)
TransferFunction{Discrete{Int64}, ControlSystems.SisoRational{Float64}}   
2.0z^4 + 1.0z^3
---------------
2.0z^6 + 1.0z^5

Sample Time: 2 (seconds)
Discrete-time transfer function model
```
