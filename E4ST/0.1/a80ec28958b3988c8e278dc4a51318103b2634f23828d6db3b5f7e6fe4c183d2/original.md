```
MaxYearly(cols...) <: Function
```

This function returns the maximum yearly value.

$$
\max_{y \in \text{yr\_idxs}} \sum_{i \in \text{idxs}, h \in \text{hr\_idxs}} \prod_{c \in \text{cols}} \text{table}[i, c][y, h]
$$
