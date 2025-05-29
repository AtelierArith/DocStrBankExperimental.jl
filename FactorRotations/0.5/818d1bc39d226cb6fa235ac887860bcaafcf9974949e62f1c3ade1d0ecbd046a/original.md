```
Oblimax(; orthogonal = false)
```

The *Oblimax* rotation method.

## Keyword arguments

  * `orthogonal`: If `orthogonal = true` an orthogonal rotation is performed, an oblique  rotation otherwise. (default: `false`)

## Details

The *Oblimax* rotation method is equivalent to [`Quartimax`](@ref) for orthogonal rotation.

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

julia> L_oblimax = rotate(L, Oblimax(orthogonal = true));

julia> L_quartimax = rotate(L, Quartimax());

julia> isapprox(loadings(L_oblimax), loadings(L_quartimax), atol = 1e-6)
true
```
