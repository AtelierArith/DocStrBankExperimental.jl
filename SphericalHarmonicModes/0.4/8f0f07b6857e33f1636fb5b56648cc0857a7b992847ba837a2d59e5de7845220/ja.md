```
l_range(mr::SphericalHarmonicModes.SHModeRange, m::Integer)
```

イテレータによってスパンされる `l` の範囲のサブセクションを返します。このとき `(l,m)` が有効な球面調和モードである必要があります。

# 例

```jldoctest
julia> r = LM(1:2, 1:2);

julia> collect(r)
3-element Vector{Tuple{Int64, Int64}}:
 (1, 1)
 (2, 1)
 (2, 2)

julia> l_range(r, 1)
1:2

julia> l_range(r, 2)
2:2
```
