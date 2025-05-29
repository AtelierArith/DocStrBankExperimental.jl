```
RemoteSemaphore(n::Int, pid=myid())
```

A semaphore living on a specific process. Do not attempt to fetch the future to a different process and use it there, as that will be an isolated, unsynced copy of the semaphore.
