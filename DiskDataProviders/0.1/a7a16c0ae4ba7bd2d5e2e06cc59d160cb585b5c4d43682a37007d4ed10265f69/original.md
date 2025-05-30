```
batchview(d::AbstractDiskDataProvider, size=d.batchsize; kwargs...)
```

Create a batch iterator that iterates batches with the batch size defined at the creation of the DiskDataProvider.
