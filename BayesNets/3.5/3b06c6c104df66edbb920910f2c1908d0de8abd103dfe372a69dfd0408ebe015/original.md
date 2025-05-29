```
statistics(
    targetind::Int,
    parents::AbstractVector{Int},
    ncategories::AbstractVector{Int},
    data::AbstractMatrix{Int}
    )
```

outputs a sufficient statistics table for the target variable that is r × q where r = ncategories[i] is the number of variable instantiations and q is the number of parental instantiations of variable i

The r-values are ordered from 1 → ncategories[i] The q-values are ordered in the same ordering as ind2sub() in Julia Base     Thus the instantiation of the first parent (by order given in parents[i])     is varied the fastest.

ex:     Variable 1 has parents 2 and 3, with r₁ = 2, r₂ = 2, r₃ = 3     q for variable 1 is q = r₂×r₃ = 6     N will be a 6×2 matrix where:         N[1,1] is the number of time v₁ = 1, v₂ = 1, v₃ = 1         N[2,1] is the number of time v₁ = 1, v₂ = 2, v₃ = 1         N[3,1] is the number of time v₁ = 1, v₂ = 1, v₃ = 2         N[4,1] is the number of time v₁ = 1, v₂ = 2, v₃ = 2         N[5,1] is the number of time v₁ = 1, v₂ = 1, v₃ = 3         N[6,1] is the number of time v₁ = 1, v₂ = 2, v₃ = 3         N[6,2] is the number of time v₁ = 2, v₂ = 1, v₃ = 1         ...
