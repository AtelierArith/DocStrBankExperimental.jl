```
uconvert(a::Units, x::Quantity{T,D,U}) where {T,D,U}
```

異なる単位に [`Unitful.Quantity`](@ref) を変換します。ターゲット単位 `a` が量 `x` の次元と異なる次元を持つ場合、変換は失敗します。このメソッドを使用して、`N m` と `J` のように同じ単位の同等の表現間で切り替えることができます。

例:

```jldoctest
julia> uconvert(u"hr",3602u"s")
1801//1800 hr

julia> uconvert(u"J",1.0u"N*m")
1.0 J
```
