```
Architectures.Arch(backend::Backend, comm::MPI.Comm, dims; device_id=nothing, gpu_aware=true)
```

Create a distributed Architecture using backend `backend` and `comm`. For GPU backends, device will be selected automatically based on a process id within a node, unless specified by `device_id`.

# Arguments

  * `backend::Backend`: The backend to use for the architecture.
  * `comm::MPI.Comm`: The MPI communicator to use for the architecture.
  * `dims`: The dimensions of the architecture.

# Keyword Arguments

  * `device_id`: The ID of the device to use. If not provided, the shared rank of the topology plus one is used.
  * `gpu_aware`: Whether the MPI implementation is GPU-aware. If not provided, defaults to `true`. Only applies to compatible backends.
