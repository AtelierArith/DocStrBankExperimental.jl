```
MinHourly(cols...) <: Function
```

この関数は、最小の時間ごとの値を返します。

$$
\min_{y \in \text{yr\_idxs}, h \in \text{hr\_idxs}} \sum_{i \in \text{idxs}} \prod_{c \in \text{cols}} \text{table}[i, c][y, h]
$$
