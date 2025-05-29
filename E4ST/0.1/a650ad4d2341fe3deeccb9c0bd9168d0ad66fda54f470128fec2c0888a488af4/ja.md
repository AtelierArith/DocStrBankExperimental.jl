```
AverageHourly(cols...) <: Function
```

結果の数式で使用される関数。各年と時間の各インデックスに対して、列の積の合計を計算し、時間の数で割ります。

$$
\frac{\sum_{i \in \text{idxs}} \sum_{y \in \text{yr\_idxs}} \prod_{c \in \text{cols}} \text{table}[i, c][y]}{\sum_{y \in \text{yr\_idxs}, h \in \text{hr\_idxs}} w_{h}}
$$
