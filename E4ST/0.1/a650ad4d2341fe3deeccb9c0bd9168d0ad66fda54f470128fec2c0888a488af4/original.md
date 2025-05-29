```
AverageHourly(cols...) <: Function
```

Function used in results formulas.  Computes the sum of the products of the columns for each index in idxs for each year and hour, divided by the number of hours.

$$
\frac{\sum_{i \in \text{idxs}} \sum_{y \in \text{yr\_idxs}} \prod_{c \in \text{cols}} \text{table}[i, c][y]}{\sum_{y \in \text{yr\_idxs}, h \in \text{hr\_idxs}} w_{h}}
$$
