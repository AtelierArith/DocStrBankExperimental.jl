```
softmax(x::AbstractArray{<:Real}; dims=:)
```

`x`の次元`dims`にわたる[ソフトマックス変換](https://en.wikipedia.org/wiki/Softmax_function)を返します。

つまり、与えられた次元にわたって合計が1になるように正規化された`exp.(x)`を返します。

関連: [`softmax!`](@ref)
