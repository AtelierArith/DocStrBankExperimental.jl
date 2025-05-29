```
decode_hilbert_zero!(ha::HilbertAlgorithm{T}}, X::Vector{A}, h::T)
```

ヒルベルトインデックス `h` に基づいて、n次元座標 `X` を計算します。ヒルベルトインデックスの型は、軸ベクトル `X` のすべての次元のビットを含むのに十分大きいです。
