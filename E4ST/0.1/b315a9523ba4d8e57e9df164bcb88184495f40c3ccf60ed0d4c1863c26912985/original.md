```
MinHourly(cols...) <: Function
```

This function returns the minimum hourly value.

$$
\min_{y \in \text{yr\_idxs}, h \in \text{hr\_idxs}} \sum_{i \in \text{idxs}} \prod_{c \in \text{cols}} \text{table}[i, c][y, h]
$$
