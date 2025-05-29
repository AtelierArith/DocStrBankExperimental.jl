```
t8_cmesh_trees_add_tree(trees, ltree_id, proc, eclass)
```

Add a tree to a trees structure.

# Arguments

  * `trees`:[in,out] The trees structure to be updated.
  * `tree_id`:[in] The local id of the tree to be inserted.
  * `proc`:[in] The mpirank of the process from which the tree was received.
  * `eclass`:[in] The tree's element class.

### Prototype

```c
void t8_cmesh_trees_add_tree (t8_cmesh_trees_t trees, t8_locidx_t ltree_id, int proc, t8_eclass_t eclass);
```
