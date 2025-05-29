```
t8_cmesh_uniform_bounds(cmesh, level, ts, first_local_tree, child_in_tree_begin, last_local_tree, child_in_tree_end, first_tree_shared)
```

Calculate the section of a uniform forest for the current rank.

# Arguments

  * `cmesh`:[in] The cmesh to be considered.
  * `level`:[in] The uniform refinement level to be created.
  * `ts`:[in] The element scheme for which to compute the bounds.
  * `first_local_tree`:[out] The first tree that contains elements belonging to the calling processor.
  * `child_in_tree_begin`:[out] The global index of the first element belonging to the calling processor. Not computed if NULL.
  * `last_local_tree`:[out] The last tree that contains elements belonging to the calling processor.
  * `child_in_tree_end`:[out] The global index of the first element that does not belonging to the calling processor anymore. Not computed if NULL.
  * `first_tree_shared`:[out] If not NULL, 1 or 0 is stored here depending on whether *first*local*tree* is the same as *last*local*tree* on the next process. *cmesh* must be committed before calling this function. *

### Prototype

```c
void t8_cmesh_uniform_bounds (t8_cmesh_t cmesh, int level, const t8_scheme_cxx_t *ts, t8_gloidx_t *first_local_tree, t8_gloidx_t *child_in_tree_begin, t8_gloidx_t *last_local_tree, t8_gloidx_t *child_in_tree_end, int8_t *first_tree_shared);
```
