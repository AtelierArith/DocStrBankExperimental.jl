```
t8_profile
```

| Field                      | Note                                                                                                                  |
|:-------------------------- |:--------------------------------------------------------------------------------------------------------------------- |
| partition_elements_shipped | The number of elements this process has sent to other in the last partition call.                                     |
| partition_elements_recv    | The number of elements this process has received from other in the last partition call.                               |
| partition_bytes_sent       | The total number of bytes sent to other processes in the last partition call.                                         |
| partition_procs_sent       | The number of different processes this process has send local elements to in the last partition call.                 |
| ghosts_shipped             | The number of ghost elements this process has sent to other processes.                                                |
| ghosts_received            | The number of ghost elements this process has received from other processes.                                          |
| ghosts_remotes             | The number of processes this process have sent ghost elements to (and received from).                                 |
| balance_rounds             | The number of iterations during balance.                                                                              |
| adapt_runtime              | The runtime of the last call to [`t8_forest_adapt`](@ref) (not counting adaptation in [`t8_forest_balance`](@ref)).   |
| partition_runtime          | The runtime of the last call to [`t8_cmesh_partition`](@ref) (not count in partition in [`t8_forest_balance`](@ref)). |
| ghost_runtime              | The runtime of the last call to [`t8_forest_ghost_create`](@ref).                                                     |
| ghost_waittime             | Amount of synchronisation time in ghost.                                                                              |
| balance_runtime            | The runtime of the last call to [`t8_forest_balance`](@ref).                                                          |
| commit_runtime             | The runtime of the last call to [`t8_cmesh_commit`](@ref).                                                            |
