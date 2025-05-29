```
Sum(cols...) <: Function
```

Function used in results formulas.  Computes the sum of the product of the column for each index in idxs

$$
\sum_{i \in \text{idxs}} \prod_{c \in \text{cols}} \text{table}[i, c]
$$
