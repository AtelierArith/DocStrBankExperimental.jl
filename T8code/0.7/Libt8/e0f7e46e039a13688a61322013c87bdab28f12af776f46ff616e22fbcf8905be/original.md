```
t8_cmesh_get_partition_table(cmesh)
```

Return the shared memory array storing the partition table of a partitioned cmesh.

# Arguments

  * `cmesh`:[in] The cmesh.

# Returns

The partition array. NULL if the cmesh is not partitioned or the partition array is not stored in *cmesh*. *cmesh* must be committed before calling this function.

### Prototype

```c
t8_shmem_array_t t8_cmesh_get_partition_table (t8_cmesh_t cmesh);
```
