```
quaternion_algebra(K::Field, a, b) -> QuaternionAlgebra
```

Return the quaternion algebra $(a, b | K)$ defined by $i^2 = a$, $j^2 = b$.

At the moment, the field must have characteristic not equal to $2$.

# Examples

```jldoctest
julia> Q = quaternion_algebra(QQ, -1, -1)
Quaternion algebra
  over rational field
  defined by i^2 = -1, j^2 = -1

julia> K, sqrt2 = quadratic_field(2);

julia> Q = quaternion_algebra(K, sqrt2, -1)
Quaternion algebra
  over real quadratic field defined by x^2 - 2
  defined by i^2 = sqrt(2), j^2 = -1
```
