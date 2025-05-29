```
is_subset(I::PBWAlgIdeal{D, T, S}, J::PBWAlgIdeal{D, T, S}) where {D, T, S}
```

`I` が `J` に含まれている場合は `true` を返し、そうでない場合は `false` を返します。

# 例

```jldoctest
julia> D, (x, dx) = weyl_algebra(QQ, [:x]);

julia> I = left_ideal(D, [dx^2])
left_ideal(dx^2)

julia> J = left_ideal(D, [x*dx^4, x^3*dx^2])
left_ideal(x*dx^4, x^3*dx^2)

julia> is_subset(I, J)
true
```
