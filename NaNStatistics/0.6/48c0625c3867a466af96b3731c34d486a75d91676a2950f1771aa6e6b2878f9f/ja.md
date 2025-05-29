```julia
nancor(X::AbstractMatrix; dims::Int=1)
```

行列 `X` の (ピアソンの積率) 相関行列を次元 `dims` に沿って計算します。`Statistics.cor` と同様ですが、`NaN` を無視します。
