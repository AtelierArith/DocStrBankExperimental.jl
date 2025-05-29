```
efs(x1, x2)
```

Calculate effect sizes.

# Arguments

  * `x1::AbstractVector`
  * `x2::AbstractVector`

# Returns

Named tuple containing:

  * `d::Float64`: Cohen's d
  * `g::Float64`: Hedges g, uses maximum likelihood estimator by Hedges and Olkin
  * `Δ::Float64`: Glass' Δ
