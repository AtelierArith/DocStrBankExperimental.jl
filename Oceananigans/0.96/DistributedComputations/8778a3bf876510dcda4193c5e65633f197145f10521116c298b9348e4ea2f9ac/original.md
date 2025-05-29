```
Distributed(child_architecture = CPU();
            partition = Partition(MPI.Comm_size(communicator)),
            devices = nothing,
            communicator = MPI.COMM_WORLD,
            synchronized_communication = false)
```

Return a distributed architecture that uses MPI for communications.

# Positional arguments

  * `child_architecture`: Specifies whether the computation is performed on CPUs or GPUs.                       Default: `CPU()`.

# Keyword arguments

  * `partition`: A [`Partition`](@ref) specifying the total processors in the `x`, `y`, and `z` direction.              Note that support for distributed `z` direction is  limited; we strongly suggest              using partition with `z = 1` kwarg.
  * `devices`: `GPU` device linked to local rank. The GPU will be assigned based on the            local node rank as such `devices[node_rank]`. Make sure to run `--ntasks-per-node` <= `--gres=gpu`.            If `nothing`, the devices will be assigned automatically based on the available resources.            This argument is irrelevant if `child_architecture = CPU()`.
  * `communicator`: the MPI communicator that orchestrates data transfer between nodes.                 Default: `MPI.COMM_WORLD`.
  * `synchronized_communication`: This keyword argument can be used to control downstream code behavior.                               If `true`, then downstream code may use this tag to toggle between an algorithm                               that permits communication between nodes "asynchronously" with other computations,                               and an alternative serial algorithm in which communication and computation are                               "synchronous" (that is, performed one after the other).                               Default: `false`, specifying the use of asynchronous algorithms where supported,                               which may result in faster time-to-solution.
