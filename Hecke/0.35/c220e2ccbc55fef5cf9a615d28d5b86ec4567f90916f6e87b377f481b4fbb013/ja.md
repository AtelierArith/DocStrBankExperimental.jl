```
quaternion_algebra(K::Field, a, b) -> QuaternionAlgebra
```

$$
K
$$

上で定義された四元数代数$(a, b | K)$を返します。ここで、$i^2 = a$、$j^2 = b$です。

現在のところ、体の特性は$2$と等しくない必要があります。

# 例

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
