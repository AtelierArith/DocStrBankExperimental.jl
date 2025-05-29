```
Risk(α::Real;
     offset::Union{Dict{Leaf,Float64},Nothing}=nothing,
     bound::Union{Real,Nothing}=nothing,
     penalty::Union{Real,Nothing} = nothing)
```

Define the CVaR risk constraint to be applied to the accumulated profits at the leaf nodes.

### Required Arguments

`λ` is weighting applied for the risk measure (max sum of weightings should be 1.0), if sum of weightings is less than 1.0, expected value will make up the rest.

`α` is the probability in the tail of the distribution

### Optional Arguments

`offset` applies a negative offset to each leaf node. This can be used to reorder the outcomes prior to applying the risk measure.

`bound` if used, this will create a constraint on CVaR(α) with this as the upper bound.

`penalty` if a constraint on CVaR is applied, then the marginal cost of violating the constraint is `penalty`; if set to `nothing` then no constraint violation is allowed.
