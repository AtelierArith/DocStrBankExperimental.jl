```
contains(I::sideal{S}, J::sideal{S}) where S
```

理想 $I$ が理想 $J$ を含む場合は `true` を返します。$I$ がグレブナー理想でない場合、標準基底を計算する必要があるため、これは高コストになります。

# 例

```jldoctest
julia> R, (x , y) = polynomial_ring(QQ, ["x", "y"])
(Singular polynomial ring (QQ),(x,y),(dp(2),C), spoly{n_Q}[x, y])

julia> I = Ideal(R, x^2 + 1, x*y)
Singular ideal over Singular polynomial ring (QQ),(x,y),(dp(2),C) with generators (x^2 + 1, x*y)

julia> J = Ideal(R, x^2 + 1)
Singular ideal over Singular polynomial ring (QQ),(x,y),(dp(2),C) with generators (x^2 + 1)

julia> contains(I, J) == true
true
```
