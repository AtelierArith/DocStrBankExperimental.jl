```
t8_cmesh_trees_add_ghost(trees, lghost_index, gtree_id, proc, eclass, num_local_trees)
```

Add a ghost to a trees structure.

# Arguments

  * `trees`:[in,out] The trees structure to be updated.
  * `ghost_index`:[in] The index in the part array of the ghost to be inserted.
  * `tree_id`:[in] The global index of the ghost.
  * `proc`:[in] The mpirank of the process from which the ghost was received.
  * `eclass`:[in] The ghost's element class.
  * `num_local_trees`:[in] The number of local trees in the cmesh.

### Prototype

```c
void t8_cmesh_trees_add_ghost (t8_cmesh_trees_t trees, t8_locidx_t lghost_index, t8_gloidx_t gtree_id, int proc, t8_eclass_t eclass, t8_locidx_t num_local_trees);
```
