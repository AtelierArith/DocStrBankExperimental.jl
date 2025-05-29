```
group_sum(groups::GroupParam,P::AbstractVector)
```

Given a `GroupParam` and a Vector `P` for group data, it will return a Vector `p` of component data, where:

pᵢ = ∑Pₖνᵢₖ

where `νᵢₖ` is the number of groups `k` at component `i`.
