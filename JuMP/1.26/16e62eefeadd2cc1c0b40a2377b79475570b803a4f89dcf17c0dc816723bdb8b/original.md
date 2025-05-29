```
moi_set(constraint::AbstractConstraint)
```

Return the set of the constraint `constraint` in the function-in-set form as a `MathOptInterface.AbstractSet`.

```
moi_set(s::AbstractVectorSet, dim::Int)
```

Returns the MOI set of dimension `dim` corresponding to the JuMP set `s`.

```
moi_set(s::AbstractScalarSet)
```

Returns the MOI set corresponding to the JuMP set `s`.
