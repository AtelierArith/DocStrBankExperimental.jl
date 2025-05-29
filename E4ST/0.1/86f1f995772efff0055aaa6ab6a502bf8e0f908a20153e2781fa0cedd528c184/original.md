```
MaxSingleLineHourly(cols...) <: Function
```

This function is made specially for the InterfaceLimit Modification, calculating the maximum single line's power flow

$$
\max_{y \in \text{yr\_idxs}, h \in \text{hr\_idxs}} \sum_{i \in \text{idxs}} \prod_{c \in \text{cols}} \text{table}[i, c][y, h]
$$
