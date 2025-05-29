```
t8_cmesh_set_partition_offsets(cmesh, tree_offsets)
```

Declare if the cmesh is understood as a partitioned cmesh and specify the first local tree for each process. This call is only valid when the cmesh is not yet committed via a call to t8*cmesh*commit. If instead t8*cmesh*set*partition*range was called and the cmesh is derived then the offset array is constructed during commit.

# Arguments

  * `cmesh`:[in,out] The cmesh to be updated.
  * `tree_offsets`:[in] An array of global tree_id offsets for each process can be specified here. TODO: document flag for shared trees.

### Prototype

```c
void t8_cmesh_set_partition_offsets (t8_cmesh_t cmesh, t8_shmem_array_t tree_offsets);
```
