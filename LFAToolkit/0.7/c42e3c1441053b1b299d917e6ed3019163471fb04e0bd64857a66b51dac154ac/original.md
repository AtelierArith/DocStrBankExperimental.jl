```julia
sausage_transformation(d)
```

Compute the conformal mapping of Gauss ellipses to sausage_transformations using a truncated Taylor expansion of arcsin(s). See Figure 4.1 of Hale and Trefethen (2008).

# Arguments:

  * `d::Int`:  polynomial degree of truncated Taylor series expansion of arcsin(s).

# Returns:

  * conformal mapping

# Example:

```jldoctest
# sausage_transformation conformal map
g, gprime = LFAToolkit.sausage_transformation(9);

# verify
truegonrange = [
    -0.9999999999999999,
    -0.39765215163451934,
    0.0,
    0.39765215163451934,
    0.9999999999999999,
];
@assert g.(LinRange(-1, 1, 5)) ≈ truegonrange

# output

```
