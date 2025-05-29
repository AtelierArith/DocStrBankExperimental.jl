```
t8_cmesh_trees_init(ptrees, num_procs, num_trees, num_ghosts)
```

Initialize a trees structure and allocate its parts. This function allocates the from_procs array without filling it, it also allocates the tree_to_proc and ghost_to_proc arrays. No memory for trees or ghosts is allocated.

# Arguments

  * `[in,ou`: ptrees The trees structure to be initialized.
  * `num_procs`:[in] The number of entries of its from_proc array (can be different for each process).
  * `num_trees`:[in] The number of trees that will be stored in this structure.
  * `num_ghosts`:[in] The number of ghosts that will be stored in this structure.

### Prototype

```c
void t8_cmesh_trees_init (t8_cmesh_trees_t *ptrees, int num_procs, t8_locidx_t num_trees, t8_locidx_t num_ghosts);
```
