```
invbitpermute!(x::AbstractArray{T}, P::AbstractBitPermutation{T})
```

各要素のビットの逆順置換を `AbstractBitPermutation` を使用して `x` に対してインプレースで実行します。つまり、配列 `x` を変更します。

関連情報は [`invbitpermute`](@ref) を参照してください。
