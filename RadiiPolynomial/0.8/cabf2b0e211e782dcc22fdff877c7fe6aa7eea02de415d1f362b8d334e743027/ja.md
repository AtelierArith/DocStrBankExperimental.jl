```
integrate!(c::Sequence, a::Sequence, α=1)
```

`a`の`α`-次積分を計算します。結果は`c`に上書きされて保存されます。

参照: [`integrate`](@ref), [`Integral`](@ref), [`*(::Integral, ::Sequence)`](@ref) および [`(::Integral)(::Sequence)`](@ref).
