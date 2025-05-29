```
elem_type(parent)
elem_type(parent_type)
```

Given a parent object (or its type), return the type of its elements.

# Examples

```jldoctest
julia> S, x = power_series_ring(QQ, 2, :x)
(Univariate power series ring over rationals, x + O(x^3))

julia> elem_type(S) == typeof(x)
true
```
