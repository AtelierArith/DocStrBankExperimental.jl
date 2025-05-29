```
proportionmap(x)
proportionmap(x::AbstractVector, w::AbstractVector{<:Real})
```

各ユニークな値を `x` におけるその比率にマッピングする辞書を返します。

重みのベクトル `wv` が提供される場合、重みの比率が生のカウントの比率ではなく計算されます。
