```
absvec(q)
```

Square-root of the sum of the squares of the "vector" components of the quaternion.

This function uses Julia's built-in `hypot` function to avoid overflow and underflow.

# Examples

```jldoctest
julia> absvec(quaternion(1,2,3,6))
7.0
```
