```
t8_cmesh_get_next_tree(cmesh, tree)
```

Given a local tree in a cmesh return a pointer to the next local tree.

# Arguments

  * `cmesh`:[in] The cmesh to be queried.
  * `tree`:[in] A local tree in *cmesh*.

# Returns

A pointer to the next local tree in *cmesh* after *tree*. If no such tree exists, NULL is returned. * *cmesh* must be committed before calling this function. TODO: If we run over tree numbers only, don't use ctree_t in API if possible.

### Prototype

```c
t8_ctree_t t8_cmesh_get_next_tree (t8_cmesh_t cmesh, t8_ctree_t tree);
```
