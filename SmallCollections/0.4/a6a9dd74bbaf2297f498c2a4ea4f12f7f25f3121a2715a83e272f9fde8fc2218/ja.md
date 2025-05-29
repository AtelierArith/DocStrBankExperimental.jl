```
addindex(v::V, x, i::Integer) where V <: AbstractCapacityVector -> V
```

`v`の`i`-番目の成分に`x`を加え、新しいベクトルを返します。

[`setindex`](@ref setindex(::AbstractCapacityVector, ::Any, i::Integer))も参照してください。
