```
proportionmap(x)
proportionmap(x::AbstractVector, w::AbstractVector{<:Real})
```

`x`内の各ユニークな値をその割合にマッピングする辞書を返します。

重みのベクトル`wv`が提供される場合、原始的なカウントの割合ではなく、重みの割合が計算されます。
