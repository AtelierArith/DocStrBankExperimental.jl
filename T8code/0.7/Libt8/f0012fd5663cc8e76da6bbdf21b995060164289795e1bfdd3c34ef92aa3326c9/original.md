```
t8_cprofile
```

This struct is used to profile cmesh algorithms. The cmesh struct stores a pointer to a profile struct, and if it is nonzero, various runtimes and data measurements are stored here.

| Field                       | Note                                                                                                         |
|:--------------------------- |:------------------------------------------------------------------------------------------------------------ |
| partition_trees_shipped     | The number of trees this process has sent to other in the last partition call.                               |
| partition_ghosts_shipped    | The number of ghosts this process has sent to other in the last partition call.                              |
| partition_trees_recv        | The number of trees this process has received from other in the last partition call.                         |
| partition_ghosts_recv       | The number of ghosts this process has received from other in the last partition call.                        |
| partition_bytes_sent        | The total number of bytes sent to other processes in the last partition call.                                |
| partition_procs_sent        | The number of different processes this process has send local trees or ghosts to in the last partition call. |
| first_tree_shared           | 1 if this processes' first tree is shared. 0 if not.                                                         |
| partition_runtime           | The runtime of the last call to [`t8_cmesh_partition`](@ref).                                                |
| commit_runtime              | The runtime of the last call to [`t8_cmesh_commit`](@ref).                                                   |
| geometry_evaluate_num_calls | The number of calls to [`t8_geometry_evaluate`](@ref).                                                       |
| geometry_evaluate_runtime   | The accumulated runtime of calls to [`t8_geometry_evaluate`](@ref).                                          |

# See also

[`t8_cmesh_set_profiling`](@ref) and, [`t8_cmesh_print_profile`](@ref)
