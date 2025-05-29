```
group_sum(groups::GroupParam,P::SingleParameter)
```

Given a `GroupParam` and a Single Parameter `P` for group data, it will return a single parameter `p` of component data, where:

pᵢ = ∑Pₖνᵢₖ

where `νᵢₖ` is the number of groups `k` at component `i`.
