```
group_pairmean(groups::GroupParam,param::PairParam)
group_pairmean(f,groups::GroupParam,param::SingleParam)
```

Given a `GroupParam` and a parameter `P` it will return a single parameter `p` of component data, where:

pᵢ = ∑νᵢₖ(∑(νᵢₗ*P(i,j))) / ∑νᵢₖ(∑νᵢₗ)

where `νᵢₖ` is the number of groups `k` at component `i` and `P(i,j)` depends on the type of `P`:

  * if `P` is a single paremeter, then `P(i,j) = f(P[i],P[j])`
  * if `P` is a pair paremeter, then `P(i,j) = p[i,j]`
