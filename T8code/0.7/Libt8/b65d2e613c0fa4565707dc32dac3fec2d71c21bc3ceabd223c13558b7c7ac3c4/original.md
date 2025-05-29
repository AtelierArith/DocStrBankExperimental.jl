```
t8_cmesh_is_partitioned(cmesh)
```

Query whether a committed cmesh is partitioned or replicated.

# Arguments

  * `cmesh`:[in] A committed cmesh.

# Returns

True if *cmesh* is partitioned. False otherwise. *cmesh* must be committed before calling this function.

### Prototype

```c
int t8_cmesh_is_partitioned (t8_cmesh_t cmesh);
```
