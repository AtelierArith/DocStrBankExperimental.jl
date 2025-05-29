```
dimension(x::Number)
dimension(x::Type{T}) where {T<:Number}
```

普通の数値が次元を持たないことを示す `Unitful.Dimensions{()}` オブジェクトを返します。これはシングルトンであり、`NoDims` としてエクスポートします。次元は空の文字列として表示されます。

例:

```jldoctest
julia> typeof(dimension(1.0))
Unitful.Dimensions{()}

julia> typeof(dimension(Float64))
Unitful.Dimensions{()}

julia> dimension(1.0) == NoDims
true
```
