```
SumMaxHourly(cols...) <: Function
```

この関数は、各最大時間値の合計を返します。

$$
\sum_{i \in \text{idxs}} \max_{y \in \text{yr\_idxs}, h \in \text{hr\_idxs}} \prod_{c \in \text{cols}} \text{table}[i, c][y, h]
$$
