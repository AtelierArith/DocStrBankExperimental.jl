```
MinYearly(cols...) <: Function
```

This function returns the minimum yearly value.

$$
\min_{y \in \text{yr\_idxs}} \sum_{i \in \text{idxs}, h \in \text{hr\_idxs}} \prod_{c \in \text{cols}} \text{table}[i, c][y, h]
$$
