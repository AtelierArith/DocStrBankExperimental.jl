```
t8_cmesh_get_first_treeid(cmesh)
```

Return the global index of the first local tree of a cmesh. If the cmesh is not partitioned this is always 0.

# Arguments

  * `cmesh`:[in] The cmesh to be considered.

# Returns

The global id of the first local tree in cmesh. *cmesh* must be committed before calling this function.

### Prototype

```c
t8_gloidx_t t8_cmesh_get_first_treeid (t8_cmesh_t cmesh);
```
