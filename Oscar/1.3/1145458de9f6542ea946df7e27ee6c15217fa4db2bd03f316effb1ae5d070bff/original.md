```
is_subset(I::PBWAlgIdeal{D, T, S}, J::PBWAlgIdeal{D, T, S}) where {D, T, S}
```

Return `true` if `I` is contained in `J`, `false` otherwise.

# Examples

```jldoctest
julia> D, (x, dx) = weyl_algebra(QQ, [:x]);

julia> I = left_ideal(D, [dx^2])
left_ideal(dx^2)

julia> J = left_ideal(D, [x*dx^4, x^3*dx^2])
left_ideal(x*dx^4, x^3*dx^2)

julia> is_subset(I, J)
true
```
