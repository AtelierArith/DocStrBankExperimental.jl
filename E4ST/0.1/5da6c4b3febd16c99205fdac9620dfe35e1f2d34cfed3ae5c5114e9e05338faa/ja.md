```
SumMinHourly(cols...) <: Function
```

この関数は、各最小時間値の合計を返します。

$$
\sum_{i \in \text{idxs}} \min_{y \in \text{yr\_idxs}, h \in \text{hr\_idxs}} \prod_{c \in \text{cols}} \text{table}[i, c][y, h]
$$
