```
t8_cmesh_trees_destroy(trees)
```

Free all memory allocated with a trees structure. This means that all coarse trees and ghosts, their face neighbor entries and attributes and the additional structures of trees are freed.

# Arguments

  * `trees`:[in,out] The tree structure to be destroyed. Set to NULL on output.

### Prototype

```c
void t8_cmesh_trees_destroy (t8_cmesh_trees_t *trees);
```
