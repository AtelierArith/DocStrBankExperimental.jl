```
t8_cmesh_trees_start_part(trees, proc, lfirst_tree, num_trees, lfirst_ghost, num_ghosts, alloc)
```

Allocate the first_tree array of a given tree_part in a tree struct with a given number of trees and ghosts. This function allocates the memory for the trees and the ghosts but not for their face neighbor entries or attributes. These must be allocated later when the eclasses of the trees and ghosts are known t8*cmesh*trees*finish*part.

# Arguments

  * `trees`:[in,out] The trees structure to be updated.
  * `proc`:[in] The index of the part to be updated.
  * `lfirst_tree`:[in] The local id of the first tree of that part.
  * `num_trees`:[in] The number of trees of that part.
  * `lfirst_ghost`:[in] The local id of the first ghost of that part.
  * `num_ghosts`:[in] The number of ghosts of that part.
  * `alloc`:[in] If true then the first_tree array is allocated for the number of trees and ghosts. When a cmesh is copied we do not want this, so in we pass alloc = 0 then.

### Prototype

```c
void t8_cmesh_trees_start_part (t8_cmesh_trees_t trees, int proc, t8_locidx_t lfirst_tree, t8_locidx_t num_trees, t8_locidx_t lfirst_ghost, t8_locidx_t num_ghosts, int alloc);
```
