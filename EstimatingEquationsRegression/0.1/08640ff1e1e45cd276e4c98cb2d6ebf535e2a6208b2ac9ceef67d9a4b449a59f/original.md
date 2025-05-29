```
AR1Cor <: CorStruct
```

Type that represents a GEE working correlation structure in which the observations within a group are modeled as being serially correlated according to their order in the dataset, with the correlation between two observations that are j positions apart being `r^j` for a real parameter `r` that can be estimated from the data.
