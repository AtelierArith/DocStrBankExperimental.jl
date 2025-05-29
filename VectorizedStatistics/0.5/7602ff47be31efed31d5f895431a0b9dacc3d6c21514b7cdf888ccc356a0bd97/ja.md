```julia
vcor(X::AbstractMatrix; dims::Int=1, multithreaded=false)
```

行列 `X` の相関行列（ピアソンの積モーメント）を次元 `dims` に沿って計算します。`Statistics.cor` と同様ですが、ベクトル化されており（オプションで）マルチスレッド対応です。
