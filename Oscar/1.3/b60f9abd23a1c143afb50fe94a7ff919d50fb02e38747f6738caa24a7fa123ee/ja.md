```
is_zero(I::PBWAlgIdeal)
```

`I`がゼロイデアルであれば`true`を返し、そうでなければ`false`を返します。

# 例

```jldoctest
julia> D, (x, y, dx, dy) = weyl_algebra(QQ, [:x, :y])
(Weyl-algebra over rational field in variables (x, y), PBWAlgElem{QQFieldElem, Singular.n_Q}[x, y, dx, dy])

julia> I = left_ideal(D, [x, dx])
left_ideal(x, dx)

julia> is_zero(I)
false
```
