```
apply(A::GroupAction{T, L, M}, g, p)
apply!(A::GroupAction{T, L, M}, q, g, p)
```

Apply the group action induced by $g ∈ \mathcal G$ to $p ∈ \mathcal M$, where the kind of group action is indicated by the [`AbstractGroupActionType`](@ref) `T`. This can be performed in-place of `q`.
