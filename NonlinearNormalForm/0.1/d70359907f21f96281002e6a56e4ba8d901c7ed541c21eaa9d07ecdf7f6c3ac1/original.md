```
mul!(m::DAMap, F::VectorField, m1::DAMap; work_Q::Union{Quaternion,Nothing}=prep_work_Q(F))
```

Computes the Lie operator `F` acting on a `DAMap` `m1`, and stores the result in `m`. Explicity, that is `F * m = (F.x, F.Q) * (m.x, m.Q) = (F.x ⋅ ∇ m.x , F.x ⋅ ∇ m.Q + m.Q*F.Q)`

### Keyword Arguments- `work_Q`   – `Quaternion{T}` if spin is included in the vector field, else `nothing`
