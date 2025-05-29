```
SumYearly(cols...) <: Function
```

結果の数式で使用される関数です。これは、与えられた各値の積を、与えられた各年について合計する関数です。

$$
\sum_{i \in \text{idxs}} \sum_{y \in \text{yr\_idxs}} \prod_{c \in \text{cols}} \text{table}[i, c][y]
$$
