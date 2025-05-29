```
CIEDE2000 <: SemiMetric
ciede2000(x, y; metric=DE_2000())
```

画像 `a` と `b` の間の画素単位の `CIEDE2000` 色差。オプションで、`DE_2000`（デフォルト）、`DE_94`、`DE_JPC79`、`DE_CMC`、`DE_BFD`、`DE_AB`、`DE_DIN99`、`DE_DIN99d`、`DE_DIN99o` の中から選ばれたメトリックを指定できます。

## 参考文献

Sharma, G., Wu, W., and Dalal, E. N., 2005. *The CIEDE2000 color‐difference formula*.
