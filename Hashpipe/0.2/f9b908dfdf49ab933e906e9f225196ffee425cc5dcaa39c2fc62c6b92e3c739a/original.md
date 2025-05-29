```
status_attach(instance_id::Int, p_status::Ref{status_t})
```

Populate the Hashpipe status pointed to by p_status with the status values of the Hashpipe instance given (created if doesn't already exist).

Attach/create lock semaphore as well.  Return nonzero on error.
