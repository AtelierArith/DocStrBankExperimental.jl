```
t8_cmesh_get_num_trees(cmesh)
```

Return the global number of trees in a cmesh.

# Arguments

  * `cmesh`:[in] The cmesh to be considered.

# Returns

The number of trees associated to *cmesh*. *cmesh* must be committed before calling this function.

### Prototype

```c
t8_gloidx_t t8_cmesh_get_num_trees (t8_cmesh_t cmesh);
```
