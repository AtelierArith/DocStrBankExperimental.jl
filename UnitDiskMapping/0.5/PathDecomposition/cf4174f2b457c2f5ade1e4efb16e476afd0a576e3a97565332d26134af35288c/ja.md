```
pathwidth(g::AbstractGraph, method)
```

グラフ `g` の最適なパス分解を計算し、`Layout` インスタンスを返します。`method` は次のいずれかです。

```
* Greedy(; nrepeat=10)
* MinhThiTrick
```
