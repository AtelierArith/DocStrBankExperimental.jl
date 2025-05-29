```
t8_cmesh_get_first_tree(cmesh)
```

Return a pointer to the first local tree in a cmesh.

# Arguments

  * `cmesh`:[in] The cmesh to be queried.

# Returns

A pointer to the first local tree in *cmesh*. If *cmesh* has no local trees, NULL is returned. *cmesh* must be committed before calling this function.

### Prototype

```c
t8_ctree_t t8_cmesh_get_first_tree (t8_cmesh_t cmesh);
```
