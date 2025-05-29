```
parent_type(element)
parent_type(element_type)
```

Given an element (or its type), return the type of its parent object.

# Examples

```jldoctest
julia> R, x = polynomial_ring(ZZ, :x)
(Univariate polynomial ring in x over integers, x)

julia> S = matrix_space(R, 2, 2)
Matrix space of 2 rows and 2 columns
  over univariate polynomial ring in x over integers

julia> a = rand(S, 0:1, 0:1);

julia> parent_type(a) == typeof(S)
true
```
