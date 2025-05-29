```
t8_cmesh_get_num_local_trees(cmesh)
```

Return the number of local trees of a cmesh. If the cmesh is not partitioned this is equivalent to t8*cmesh*get*num*trees.

# Arguments

  * `cmesh`:[in] The cmesh to be considered.

# Returns

The number of local trees of the cmesh. *cmesh* must be committed before calling this function.

### Prototype

```c
t8_locidx_t t8_cmesh_get_num_local_trees (t8_cmesh_t cmesh);
```
