```
SumMaxHourly(cols...) <: Function
```

This function returns the sum of each of the maximum hourly values. 

$$
\sum_{i \in \text{idxs}} \max_{y \in \text{yr\_idxs}, h \in \text{hr\_idxs}} \prod_{c \in \text{cols}} \text{table}[i, c][y, h]
$$
