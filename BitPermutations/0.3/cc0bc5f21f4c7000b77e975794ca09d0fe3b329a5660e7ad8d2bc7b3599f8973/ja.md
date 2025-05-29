```
bitpermute!(x::AbstractArray{T}, P::AbstractBitPermutation{T})
```

各要素のビットを `AbstractBitPermutation` を使用してインプレースで置換します。つまり、配列 `x` を変更します。

詳細は [`bitpermute`](@ref) を参照してください。
