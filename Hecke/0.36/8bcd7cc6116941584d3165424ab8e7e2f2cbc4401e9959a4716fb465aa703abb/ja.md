```
(A::FinGenAbGroup)(a::TorQuadModuleElem)
```

`a`を基礎となるアーベル群の要素として返します。

# 例

```jldoctest
julia> R = rescale(root_lattice(:D,4),2);

julia> D = discriminant_group(R);

julia> A = abelian_group(D)
(Z/2)^2 x (Z/4)^2

julia> d = D[1]
Element
  of finite quadratic module: (Z/2)^2 x (Z/4)^2 -> Q/2Z
with components [1 0 0 0]

julia> d == D(A(d))
true
```
