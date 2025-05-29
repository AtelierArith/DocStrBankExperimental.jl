```
PropertyList{D}
```

`AbstractPropertyList`のサブタイプで、辞書の値にアクセスするための`getproperty`構文を提供します。

## 例

```jldoctest
julia> using FieldProperties

julia> m = PropertyList(; a = 1, b= 2)
PropertyList{Dict{Symbol,Any}} with 2 entries
    a: 1
    b: 2

julia> getindex(m, :a)
1

julia> get(m, :a, 3)
1

julia> get!(m, :a, 3)
1

julia> m.a
1

julia> m[:a] = 2
2

julia> m.a
2

julia> m.b
2

julia> m.b = 3
3

julia> m.b
3

julia> m.name = "ridiculously long name that we don't want to print everytime the other properties are printed.";


julia> m.suppress = (:name,)
(:name,)

julia> m
PropertyList{Dict{Symbol,Any}} with 4 entries
    a: 2
    b: 3
    name: <suppressed>
    suppress: (:name,)
```
