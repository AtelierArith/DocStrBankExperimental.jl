```
SumHourlyWeighted(cols...) <: Function
```

This is a function that adds up the product of each of the values given to it times the hour weight for each of the years and hours given.

$$
\sum_{i \in \text{idxs}} \sum_{y \in \text{yr\_idxs}} \sum_{h \in \text{hr\_idxs}} w_{h} \prod_{c \in \text{cols}} \text{table}[i, c][y, h]
$$
