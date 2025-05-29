```
rotate!(Λ, method::RotationMethod; kwargs...)
```

Perform a rotation of the factor loading matrix `Λ` and overwrite `Λ` with the rotated loading matrix.

For a list of available keyword arguments see [`rotate`](@ref).

## Examples

```jldoctest; filter = r"(\d*)\.(\d{4})\d+" => s"\1.\2"
julia> L = [
           0.830 -0.396
           0.818 -0.469
           0.777 -0.470
           0.798 -0.401
           0.786  0.500
           0.672  0.458
           0.594  0.444
           0.647  0.333
       ];

julia> rotate!(L, Quartimax())
8×2 Matrix{Float64}:
 0.898755  0.194823
 0.933943  0.129748
 0.902132  0.103864
 0.876508  0.171284
 0.315572  0.876476
 0.251124  0.773489
 0.198008  0.714678
 0.307858  0.659334

```
