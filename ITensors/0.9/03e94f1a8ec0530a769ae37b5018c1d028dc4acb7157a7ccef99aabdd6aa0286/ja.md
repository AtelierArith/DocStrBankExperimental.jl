```
replaceinds(A::ITensor, inds1, inds2) -> ITensor

replaceinds!(A::ITensor, inds1, inds2)
```

ITensor内のインデックス`inds1[n]`をインデックス`inds2[n]`に置き換えます。ここで、`n`は`1`から`length(inds1) == length(inds2)`までの範囲です。

インデックスは同じ空間を持っている必要があります（すなわち、同じ次元とQNsを持っている必要があります）。

ITensorのストレージは変更されず、コピーされることもありません（出力ITensorは入力ITensorのビューです）。
