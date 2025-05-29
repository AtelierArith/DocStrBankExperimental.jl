```
inv(q::Quaternion)
```

`q::Quaternion`の乗法逆元を返します。これにより、`q*inv(q)`または`inv(q)*q`は、丸め誤差を考慮して`one(q)`（乗法単位元）を生成します。

# 例

```jldoctest
julia> inv(quat(1))
QuaternionF64(1.0, -0.0, -0.0, -0.0)

julia> inv(quat(1, 2, 0, 0))
QuaternionF64(0.2, -0.4, -0.0, -0.0)

julia> inv(quat(2//3))
Quaternion{Rational{Int64}}(3//2, 0//1, 0//1, 0//1)
```
