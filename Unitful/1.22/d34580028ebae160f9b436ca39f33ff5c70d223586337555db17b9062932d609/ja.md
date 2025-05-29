```
DimensionlessQuantity{T,U} = AbstractQuantity{T, NoDims, U}
```

単位はあるが次元がない[`Unitful.Quantity`](@ref)型に対してディスパッチするのに便利です。（異なる10の累乗接頭辞を持つ単位はキャンセルされません。）

例:

```jldoctest
julia> isa(1.0u"mV/V", DimensionlessQuantity)
true
```
