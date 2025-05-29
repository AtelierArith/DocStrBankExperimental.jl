```
dimension(u::Units{U,D}) where {U,D}
```

単位 `D` の次元に対応する [`Unitful.Dimensions`](@ref) オブジェクトを返します。次元のない単位の組み合わせの場合、`Unitful.Dimensions{()}` オブジェクト（`NoDims`）が返されます。

例:

```jldoctest
julia> dimension(u"m")
𝐋

julia> typeof(dimension(u"m"))
Unitful.Dimensions{(Unitful.Dimension{:Length}(1//1),)}

julia> dimension(u"m/km")
NoDims
```
