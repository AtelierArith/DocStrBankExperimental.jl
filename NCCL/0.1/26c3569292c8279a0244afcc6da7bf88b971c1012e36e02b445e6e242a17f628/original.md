```
NCCL.Communicator(nranks, rank; [unique_id]) :: Communicator
```

Create a single communicator for use in a multi-threaded or multi-process environment. `nranks` is the number of ranks in the communicator, and `rank` is the 0-based index of the current rank. `unique_id` is an optional unique identifier for the communicator.

# Examples

```
comm = Communicator(length(CUDA.devices()), id, myid())
# this blocks until all other ranks have connected
```

# External links

  * [`ncclCommInitRank`](https://docs.nvidia.com/deeplearning/nccl/user-guide/docs/api/comms.html#ncclCommInitRank)
