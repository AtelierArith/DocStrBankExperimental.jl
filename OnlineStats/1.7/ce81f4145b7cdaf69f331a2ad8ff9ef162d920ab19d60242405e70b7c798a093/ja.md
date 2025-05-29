```
FastTree(p::Int, nclasses=2; stat=FitNormal(), maxsize=5000, splitsize=1000)
```

`p` 個の予測変数とクラス `1, 2, …, nclasses` の決定木を計算します。ノードは `splitsize` の観測値に達すると分割され、ツリーに `maxsize` のノードが含まれるまで続きます。各変数は `stat` によって要約され、`FitNormal()` または `Hist(nbins)` であることができます。

# 例

```
x = randn(10^5, 10)
y = rand([1,2], 10^5)

o = fit!(FastTree(10), zip(eachrow(x),y))

xi = randn(10)
classify(o, xi)
```
