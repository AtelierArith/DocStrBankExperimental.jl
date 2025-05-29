```
CollisionConstraint
```

Enforces a pairwise non self-collision constraint on the state, such that     `norm(x[x1] - x[x2]).^2 ≥ r^2`,     where `x1` and `x2` are the indices of the positions of the respective bodies and `r`     is the collision radius.

# Constructor

CollisionConstraint(n::Int, x1::AbstractVector{Int}, x2::AbstractVector{Int}, r::Real)
