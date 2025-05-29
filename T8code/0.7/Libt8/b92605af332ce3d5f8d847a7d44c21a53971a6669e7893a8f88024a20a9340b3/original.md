```
t8_cmesh_trees_init_attributes(trees, ltree_id, num_attributes, attr_bytes)
```

For one tree in a trees structure set the number of attributes and temporarily store the total size of all of this tree's attributes. This temporary value is used in t8*cmesh*trees*finish*part.

# Arguments

  * `trees`:[in,out] The trees structure to be updated.
  * `ltree_id`:[in] The local id of one tree in *trees*.
  * `num_attributes`:[in] The number of attributes of this tree.
  * `attr_bytes`:[in] The total number of bytes of all attributes of this tree.

### Prototype

```c
void t8_cmesh_trees_init_attributes (t8_cmesh_trees_t trees, t8_locidx_t ltree_id, size_t num_attributes, size_t attr_bytes);
```
