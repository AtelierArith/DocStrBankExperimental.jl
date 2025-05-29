```
t8_cmesh_trees_add_ghost_attribute(trees, attr, local_ghost_id, ghosts_inserted, index)
```

Add the next ghost attribute from stash to the correct position in the char pointer structure Since it is created from stash, all attributes are added to part 0. The following attribute offset gets updated already.

# Arguments

  * `trees`:[in,out] The trees structure, whose char array is updated.
  * `attr`:[in] The stash attribute that is added.
  * `local_ghost_id`:[in] The local ghost id.
  * `ghosts_inserted`:[in] The number of ghost that were already inserted, so that we do not write over the end.
  * `index`:[in] The attribute index of the attribute to be added.

### Prototype

```c
void t8_cmesh_trees_add_ghost_attribute (const t8_cmesh_trees_t trees, const t8_stash_attribute_struct_t *attr, t8_locidx_t local_ghost_id, t8_locidx_t ghosts_inserted, size_t index);
```
