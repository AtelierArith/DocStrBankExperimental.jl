```
clear_worker_caches!(pool::AbstractWorkerPool)
```

Clear the worker caches (cached function closures, etc.) on the workers In `pool`.

Does nothing if the pool doesn't perform any on-worker caching.
