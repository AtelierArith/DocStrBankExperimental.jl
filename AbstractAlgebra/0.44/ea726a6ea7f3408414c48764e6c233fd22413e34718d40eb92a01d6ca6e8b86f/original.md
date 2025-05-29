```
compose(f::Map, g::Map)
```

Compose the two maps $f$ and $g$, i.e. return the map $h$ such that $h(x) = g(f(x))$.

# Examples

```jldoctest
julia> f = map_from_func(x -> x + 1, ZZ, ZZ);

julia> g = map_from_func(x -> QQ(x), ZZ, QQ);

julia> h = compose(f, g)
Functional composite map
  from integers
  to rationals
which is the composite of
  Map: integers -> integers
  Map: integers -> rationals
```
