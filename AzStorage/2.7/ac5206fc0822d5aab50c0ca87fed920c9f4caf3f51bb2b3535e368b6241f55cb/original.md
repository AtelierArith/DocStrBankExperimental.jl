```
container = AzContainer("containername"; storageaccount="myacccount", kwargs...)
```

`container` is a handle to a new or existing Azure container in the `myaccount` sorage account. The storage account must already exist.

# Additional keyword arguments

  * `session=AzSession(;lazy=false,scope=offline_access+openid+https://storage.azure.com/user_impersonation)` user credentials (see AzSessions.jl package).
  * `nthreads=Sys.CPU_THREADS` number of system threads that OpenMP will use to thread I/O.
  * `connect_timeout=30` client-side timeout for connecting to the server.
  * `read_timeout=10` client-side timeout for receiving the first byte from the server.
  * `nretry=10` number of retries to the Azure service (when Azure throws a retryable error) before throwing an error.
  * `verbose=0` verbosity flag passed to libcurl.

# Notes

The container name can contain "/"'s.  If this is the case, then the string preceding the first "/" will be the container name, and the string that remains will be pre-pended to the blob names.  This allows Azure to present blobs in a pseudo-directory structure.  Note that trailing and leading `/`'s are ignored.
