```
rawview(img::AbstractArray{FixedPoint})
```

は、`img` の値がその生の基礎ストレージに基づいて解釈される「ビュー」を返します。たとえば、`img` が `Array{N0f8}` の場合、ビューは `Array{UInt8}` のように動作します。

関連情報: [`normedview`](@ref)
