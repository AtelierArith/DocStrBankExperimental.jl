```
Quartimax()
```

The *Quartimax* rotation criterion.

## Details

The *Quartimax* criterion is a special case of the [`Oblimin`](@ref) rotation criterion with parameter `gamma = 0`.

## Examples

### Setting up the criterion

```jldoctest
julia> Quartimax()
Quartimax()
```

### Testing equivalence of Quartimax and Oblimin

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

julia> L_quartimax = rotate(L, Quartimax());

julia> L_oblimin = rotate(L, Oblimin(gamma = 0, orthogonal = true));

julia> loadings(L_quartimax) ≈ loadings(L_oblimin)
true
```
