```
ppt_worker_pool()
```

Returns the default ParallelProcessingTools worker pool.

If the default instance doesn't exist yet, then a `FlexWorkerPool` will be created that initially contains `Distributed.myid()` as the only worker.
