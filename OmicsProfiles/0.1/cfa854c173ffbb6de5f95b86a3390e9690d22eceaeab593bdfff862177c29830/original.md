```
OmicsProfile(countmat, var, varindex; T=float(eltype(countmat)))
```

# Arguments

  * `countmat`: The count matrix for given omics and it will be set to key `:count`.
  * `var::DataFrame`: The dataframe contains meta information for features or variables.
  * `varindex::Symbol`: The index of dataframe `var`.
  * `T`: Element type of `countmat`.

# Examples

```jldoctest
julia> r, c = (100, 500)
(100, 500)

julia> data = rand(0:100, r, c);

julia> var = DataFrame(index=1:r, C=rand(r), D=rand(r));

julia> prof = OmicsProfile(data, var, :index)
OmicsProfile (nvar = 100):
    var: index, C, D
    layers: count
```
