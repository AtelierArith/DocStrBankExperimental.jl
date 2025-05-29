```
PoolDims(x_size::NTuple{M}, k::Union{NTuple{L, Int}, Int};
         stride=k, padding=0, dilation=1)  where {M, L}
```

任意の入力サイズ、カーネルサイズ、ストライド、拡張、チャネル数を持つ「プーリング」操作の次元。 コンパイル時に効率的な実装にディスパッチするために使用されます。
