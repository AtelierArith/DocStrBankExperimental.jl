```
struct OfDegree{D} <: Function
    degree::D
end
```

A function `d::OfDegree` is such that `d(t)` returns `degree(t) == d.degree`. Note that `!d` creates the negation. See also [`filter_terms`](@ref).
