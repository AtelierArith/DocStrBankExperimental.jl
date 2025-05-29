```
swapind(A::ITensor, i1::Index, i2::Index) -> ITensor

swapind!(A::ITensor, i1::Index, i2::Index)
```

ITensor内のインデックス`i1`をインデックス`i2`と入れ替えます。

インデックスは同じ空間（すなわち、同じ次元とQNsが必要な場合）を持っている必要があります。
