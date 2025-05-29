```
(T::TorQuadModule)(a::FinGenAbGroupElem) -> TorQuadModuleElem
```

Coerce `a` to `T`.

```jldoctest
julia> R = rescale(root_lattice(:D,4),2);

julia> T = discriminant_group(R);

julia> A = abelian_group(T)
(Z/2)^2 x (Z/4)^2

julia> a = rand(A);

julia> A(T(a)) == a
true
```
