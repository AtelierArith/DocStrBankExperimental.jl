```
softmax!(r::AbstractArray{<:Real}, x::AbstractArray{<:Real}=r; dims=:)
```

`r`を、次元`dims`にわたる`x`の[ソフトマックス変換](https://en.wikipedia.org/wiki/Softmax_function)で上書きします。

つまり、`r`は`exp.(x)`で上書きされ、指定された次元にわたって合計が1になるように正規化されます。

参照: [`softmax`](@ref)
