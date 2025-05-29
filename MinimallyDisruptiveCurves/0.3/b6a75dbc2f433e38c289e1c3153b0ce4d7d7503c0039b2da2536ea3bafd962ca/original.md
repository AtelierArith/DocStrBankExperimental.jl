```
transform_cost(cost, p0, tr::TransformationStructure; unames=nothing, pnames=nothing)
return DiffCost(new_cost, new_cost2), newp0
```

Given a cost function C(p), makes a new differentiable cost function D(q), where q = tr(p) and D(q) = C(p)
