```
stratifiedobs(d::AbstractDiskDataProvider, p::AbstractFloat, args...; kwargs...)
```

Partition the data into multiple disjoint subsets proportional to the value(s) of p. The observations are assignmed to a data subset using stratified sampling without replacement. These subsets are then returned as a Tuple of subsets, where the first element contains the fraction of observations of data that is specified by the first float in p.

For example, if p is a Float64 itself, then the return-value will be a tuple with two elements (i.e. subsets), in which the first element contains the fraction of observations specified by p and the second element contains the rest. In the following code the first subset train will contain around 70% of the observations and the second subset test the rest. The key difference to splitobs is that the class distribution in y will actively be preserved in train and test.

`train, test = stratifiedobs(diskdataprovider, 0.7)`
