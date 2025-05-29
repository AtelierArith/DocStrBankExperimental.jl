```
k_categories(n)
```

Calculate number of categories for a given sample size `n`.

# Arguments

  * `n::Int64`: sample size

# Returns

Named tuple containing:

  * `k1::Float64`: sqrt(n)
  * `k2::Float64`: 1 + 3.222 * log10(n)
