```julia
kosloff_talezer_transformation(α)
```

Compute the Kosloff and Tal-Ezer conformal map derived from the inverse sine function

# Arguments:

  * `α::Float64`:  polynomial degree of truncated Taylor series expansion of arcsin(s).

# Returns:

  * conformal mapping

# Example:

```jldoctest
# kosloff_talezer_transformation conformal map
g, gprime = LFAToolkit.kosloff_talezer_transformation(0.95);

# verify
truegonrange = [-1.0, -0.39494881426787537, 0.0, 0.39494881426787537, 1.0];
@assert g.(LinRange(-1, 1, 5)) ≈ truegonrange

# output

```
