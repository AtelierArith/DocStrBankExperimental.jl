```
lenses(t::Tuple)
lenses(nt::NamedTuple)
lenses(NT::Type{NamedTuple{K,V}})
```

与えられた値または型のためのレンズのタプルを構築します

例:     julia> nt = (a=(b=[1,2],c=(d=[3,4],e=[5,6])),f=[7,8]);

```
julia> lenses(nt)
((@lens _.a.b), (@lens _.a.c.d), (@lens _.a.c.e), (@lens _.f))

julia> lenses(typeof(nt))
((@lens _.a.b), (@lens _.a.c.d), (@lens _.a.c.e), (@lens _.f))
```
