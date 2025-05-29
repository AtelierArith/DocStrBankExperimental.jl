```
contains(I::sideal{S}, J::sideal{S}) where S
```

Return `true` if the ideal $I$ contains the ideal $J$. This will be expensive if $I$ is not a Groebner ideal, since its standard basis must be computed.

# Examples

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
