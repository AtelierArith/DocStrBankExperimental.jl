```
SumYearly(cols...) <: Function
```

Function used in results formulas.  This is a function that adds up the product of each of the values given to it for each year given.

$$
\sum_{i \in \text{idxs}} \sum_{y \in \text{yr\_idxs}} \prod_{c \in \text{cols}} \text{table}[i, c][y]
$$
