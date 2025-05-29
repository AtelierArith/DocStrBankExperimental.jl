```
MinYearly(cols...) <: Function
```

この関数は最小の年間値を返します。

$$
\min_{y \in \text{yr\_idxs}} \sum_{i \in \text{idxs}, h \in \text{hr\_idxs}} \prod_{c \in \text{cols}} \text{table}[i, c][y, h]
$$
