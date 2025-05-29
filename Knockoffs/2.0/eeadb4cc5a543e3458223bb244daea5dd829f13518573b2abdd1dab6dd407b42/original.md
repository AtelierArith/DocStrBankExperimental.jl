```
mk_threshold(τ::Vector{T}, κ::Vector{Int}, m::Int, q::Number)
```

Chooses the multiple knockoff threshold `τ̂ > 0` by setting τ̂ = min{ t > 0 : (1/m + 1/m * {#j: κ[j] ≥ 1 and W[j] ≥ t}) / {#j: κ[j] == 0 and W[j] ≥ τ̂} ≤ q }.

# Inputs

  * `τ`: τ[i] stores the feature importance score for the ith feature, i.e. the value   T0 - median(T1,...,Tm). Note in Gimenez and Zou, the max function is used    instead of median
  * `κ`: κ[i] stores which of m knockoffs has largest importance score. When original    variable has largest score, κ[i] == 0.
  * `m`: Number of knockoffs per variable generated
  * `q`: target FDR (between 0 and 1)
  * `rej_bounds`: Number of values of top τ to consider (default = 10000)

# Reference:

  * Equations 8 and 9 in supplement of "Identification of putative causal loci in    wholegenome sequencing data via knockoff statistics" by He et al.
  * Algorithm 1 of "Improving the Stability of the Knockoff Procedure: Multiple    Simultaneous Knockoffs and Entropy Maximization" by Gimenez and Zou.
