```
compose(f::Map, g::Map)
```

2つのマップ $f$ と $g$ を合成します。すなわち、$h(x) = g(f(x))$ となるマップ $h$ を返します。

# 例

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
