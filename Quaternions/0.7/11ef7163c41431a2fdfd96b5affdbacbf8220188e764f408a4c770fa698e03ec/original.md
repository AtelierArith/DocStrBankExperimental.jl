```
inv(q::Quaternion)
```

Return the multiplicative inverse of `q::Quaternion`, such that `q*inv(q)` or `inv(q)*q` yields `one(q)` (the multiplicative identity) up to roundoff errors.

# Examples

```jldoctest
julia> inv(quat(1))
QuaternionF64(1.0, -0.0, -0.0, -0.0)

julia> inv(quat(1, 2, 0, 0))
QuaternionF64(0.2, -0.4, -0.0, -0.0)

julia> inv(quat(2//3))
Quaternion{Rational{Int64}}(3//2, 0//1, 0//1, 0//1)
```
