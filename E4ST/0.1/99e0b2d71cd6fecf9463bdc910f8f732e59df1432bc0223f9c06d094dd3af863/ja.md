```
AverageHourlyWeighted(cols...) <: Function
```

結果の数式で使用される関数。各年と時間に対して、idxs内の各インデックスの列の積の合計を計算し、時間数で重み付けし、総時間数で割ります。

$$
\frac{\sum_{i \in \text{idxs}} \sum_{y \in \text{yr\_idxs}} \sum_{h \in \text{hr\_idxs}} \prod_{c \in \text{cols}} \text{table}[i, c][y]}{\sum_{y \in \text{yr\_idxs}}\sum{h \in \text{hr\_idxs}} w_{h}}
$$
