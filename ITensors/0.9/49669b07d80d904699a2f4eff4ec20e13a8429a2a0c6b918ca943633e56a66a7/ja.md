```
swapinds(A::ITensor, inds1, inds2) -> ITensor

swapinds!(A::ITensor, inds1, inds2)
```

ITensor内のインデックス`inds1[n]`をインデックス`inds2[n]`と入れ替えます。ここで、`n`は`1`から`length(inds1) == length(inds2)`までの範囲です。

インデックスは同じ空間を持っている必要があります（すなわち、同じ次元とQNsを持っている必要があります）。

ITensorのストレージは変更されず、コピーもされません（出力ITensorは入力ITensorのビューです）。
