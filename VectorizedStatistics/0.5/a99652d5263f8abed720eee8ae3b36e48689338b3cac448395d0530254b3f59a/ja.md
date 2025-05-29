```julia
vcor(x::AbstractVector, y::AbstractVector, multithreaded=false)
```

ベクトル `x` と `y` の間の（ピアソンの積モーメント）相関を計算します。`Statistics.cor` と同様ですが、ベクトル化されており（オプションで）マルチスレッド対応です。

`cov(x,y) / (std(x) * std(y))` と同等です。
