```
AverageHourlyWeighted(cols...) <: Function
```

Function used in results formulas.  Computes the sum of the products of the columns for each index in idxs for each year and hour weighted by the number of hours, divided by the total number of hours.

$$
\frac{\sum_{i \in \text{idxs}} \sum_{y \in \text{yr\_idxs}} \sum_{h \in \text{hr\_idxs}} \prod_{c \in \text{cols}} \text{table}[i, c][y]}{\sum_{y \in \text{yr\_idxs}}\sum{h \in \text{hr\_idxs}} w_{h}}
$$
