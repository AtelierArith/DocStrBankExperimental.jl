```
MaxHourly(cols...) <: Function
```

This function returns the maximum aggregated hourly value. Sums up all values for that hour over the given idxs, then takes the maximum.  Suited for results like load where you want to know the maximum of the regional load. 

$$
\max_{y \in \text{yr\_idxs}, h \in \text{hr\_idxs}} \sum_{i \in \text{idxs}} \prod_{c \in \text{cols}} \text{table}[i, c][y, h]
$$
