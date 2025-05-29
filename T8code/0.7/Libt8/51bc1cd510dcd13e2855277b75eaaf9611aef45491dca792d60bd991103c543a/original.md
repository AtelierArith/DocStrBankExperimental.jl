```
t8_cmesh_trees_copy_toproc(trees_dest, trees_src, lnum_trees, lnum_ghosts)
```

Copy the tree_to_proc and ghost_to_proc arrays of one tree structure to another one.

# Arguments

  * `trees_dest`:[in,out] The destination trees structure.
  * `trees_src`:[in] The source trees structure.
  * `lnum_trees`:[in] The total number of trees stored in *trees_src*.
  * `lnum_ghosts`:[in] The total number of ghosts stored in *trees_src*.

### Prototype

```c
void t8_cmesh_trees_copy_toproc (t8_cmesh_trees_t trees_dest, t8_cmesh_trees_t trees_src, t8_locidx_t lnum_trees, t8_locidx_t lnum_ghosts);
```
