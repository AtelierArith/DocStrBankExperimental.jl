```
ChannelDiskDataProvider{XT, YT}(xsize, batchsize, queuelength::Int; kwargs...) where {XT, YT}
```

Constructor for ChannelDiskDataProvider. `{XT, YT}` are the types of the input and output respectively.

#Arguments:

  * `xsize`: Tuple with size of each data point
  * `batchsize`: how many datapoints to put in a batch
  * `queuelength`: length of buffer, it's a good idea to make this be some integer multiple of the batch size.
  * `kwargs`: to set the other fields of the structure.
  * `transform` : A Function `(x,y)->(x,y)` or `x->x` that transforms the data point before it is put in a batch. This can be used to, e.g., apply some pre processing or normalization etc.
