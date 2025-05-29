```julia
nancor(x::AbstractVector, y::AbstractVector)
```

ベクトル `x` と `y` の間の（ピアソンの積モーメント）相関を計算します。`Statistics.cor` と同様ですが、`NaN` を無視します。

`nancov(x,y) / (nanstd(x) * nanstd(y))` と同等です。
