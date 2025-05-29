`Hom(S::Group,T::Group,images)`

builds an object representing the homomorphism from `S` to `T` which maps `gens(S)` to `images`.

```julia-repl
julia> S=Group(Perm(1,2),Perm(2,3))
Group((1,2),(2,3))

julia> T=Group(Perm(1,2))
Group((1,2))

julia> h=Hom(S,T,[T(1),T(1)])
Hom(Group((1,2),(2,3))→ Group((1,2));[(1,2), (2,3)]↦ [(1,2), (1,2)]

julia> h(S(1,2)) # the image by h
()
```
