```julia
hale_trefethen_strip_transformation(ρ)
```

Compute the Hale and Trefethen strip transformation

# Arguments:

  * `ρ::Float64`:  sum of the semiminor and semimajor axis

# Returns:

  * conformal mapping

# Example:

```jldoctest
# hale_trefethen_strip_transformation conformal map
g, gprime = hale_trefethen_strip_transformation(1.4);

# verify
truegonrange = [-1.0, -0.36812132798370184, 0.0, 0.36812132798370184, 1.0];
@assert g.(LinRange(-1, 1, 5)) ≈ truegonrange

# output

```
