```
fieldnames(x::DataType)
```

`DataType`のフィールドの名前を含むタプルを取得します。

関連情報としては、[`propertynames`](@ref)、[`hasfield`](@ref)があります。

# 例

```jldoctest
julia> fieldnames(Rational)
(:num, :den)

julia> fieldnames(typeof(1+im))
(:re, :im)
```
