```
SumHourlyWeighted(cols...) <: Function
```

これは、与えられた各値の積を、与えられた各年と時間の時間重みで掛け算して合計する関数です。

$$
\sum_{i \in \text{idxs}} \sum_{y \in \text{yr\_idxs}} \sum_{h \in \text{hr\_idxs}} w_{h} \prod_{c \in \text{cols}} \text{table}[i, c][y, h]
$$
