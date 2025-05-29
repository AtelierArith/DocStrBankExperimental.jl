```
SumMinHourly(cols...) <: Function
```

This function returns the sum of each of the minimum hourly values. 

$$
\sum_{i \in \text{idxs}} \min_{y \in \text{yr\_idxs}, h \in \text{hr\_idxs}} \prod_{c \in \text{cols}} \text{table}[i, c][y, h]
$$
