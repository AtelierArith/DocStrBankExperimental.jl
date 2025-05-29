```
allocate_array_ad(n[, m]; <keyword arguments>)
```

Allocate vector or matrix as AD with optionally provided context and a specified non-zero on the diagonal.

# Arguments

  * `n::Integer`: number of entries in vector, or number of rows if `m` is given.
  * `m::Integer`: number of rows (optional)

# Keyword arguments

  * `npartials = 1`: Number of partials derivatives to allocate for each element
  * `diag_pos = nothing`: Indices of where to put entities on the diagonal (if any)

Other keyword arguments are passed onto `get_ad_entity_scalar`.

# Examples:

Allocate a vector with a single partial:

```julia-repl
julia> allocate_array_ad(2)
2-element Vector{ForwardDiff.Dual{nothing, Float64, 1}}:
 Dual{nothing}(0.0,0.0)
 Dual{nothing}(0.0,0.0)
```

Allocate a vector with two partials, and set the first to one:

```julia-repl
julia> allocate_array_ad(2, diag_pos = 1, npartials = 2)
2-element Vector{ForwardDiff.Dual{nothing, Float64, 2}}:
 Dual{nothing}(0.0,1.0,0.0)
 Dual{nothing}(0.0,1.0,0.0)
```

Set up a matrix with two partials, where the first column has partials [1, 0] and the second [0, 1]:

```julia-repl
julia> allocate_array_ad(2, 2, diag_pos = [1, 2], npartials = 2)
2×2 Matrix{ForwardDiff.Dual{nothing, Float64, 2}}:
 Dual{nothing}(0.0,1.0,0.0)  Dual{nothing}(0.0,1.0,0.0)
 Dual{nothing}(0.0,0.0,1.0)  Dual{nothing}(0.0,0.0,1.0)
```
