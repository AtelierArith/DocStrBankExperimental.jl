```
setindex(v::V, x, i::Integer) where V <: AbstractCapacityVector -> V
```

`v`の`i`番目の要素を`x`に置き換え、新しいベクトルを返します。

また、`Base.setindex`、[`addindex`](@ref addindex(::AbstractCapacityVector, ::Any, i::Integer))も参照してください。
