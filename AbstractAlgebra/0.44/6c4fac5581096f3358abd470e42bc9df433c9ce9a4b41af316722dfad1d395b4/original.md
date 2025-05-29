```
exterior_power(A::MatElem, k::Int) -> MatElem
```

Return the `k`-th exterior power of `A`.

# Examples

```jldoctest
julia> A = matrix(ZZ, 3, 3, [1, 2, 3, 4, 5, 6, 7, 8, 9]);

julia> exterior_power(A, 2)
[-3    -6   -3]
[-6   -12   -6]
[-3    -6   -3]
```
