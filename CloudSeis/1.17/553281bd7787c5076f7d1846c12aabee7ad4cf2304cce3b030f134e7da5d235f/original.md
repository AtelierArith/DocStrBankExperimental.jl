```
I = LogicalIndices(io::CSeis)
```

Returns a construct similar to `CartesianIndices` that allows conversion from linear indices to cartesian indices that are offest by the logical starts and deltas of the CloudSeis data context.  In addition, `LogicalIndices` implements iteration for looping over all frames in a data-set.  For example,

```julia
io = csopen(AzContainer("foo"; storageaccount="bar))
idx = LogicalIndices(io)[2] # get the index corresponding to the second frame in the data-set.
for idx in LogicalIndices(io)
    @show idx
    trcs, hdrs = getframe(io, idx)
end
```
