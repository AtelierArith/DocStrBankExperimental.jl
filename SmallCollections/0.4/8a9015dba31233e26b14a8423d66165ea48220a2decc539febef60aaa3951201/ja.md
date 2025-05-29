```
insert(v::V, i::Integer, x) where V <: AbstractCapacityVector{T} -> V
```

`v`において位置`i`に`x`を挿入することによって得られる`AbstractCapacityVector`を返します。位置`i`は`1`と`length(v)+1`の間でなければなりません。

これは`Base.insert!`の非変異的なアナログです。

参照してください [`duplicate`](@ref).
