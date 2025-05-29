```
t8_forest_get_tree_class(forest, ltreeid)
```

Return the eclass of a tree in a forest.

# Arguments

  * `forest`:[in] The forest.
  * `ltreeid`:[in] The local id of a tree (local or ghost) in *forest*.

# Returns

The element class of the tree with local id *ltreeid*.

### Prototype

```c
t8_eclass_t t8_forest_get_tree_class (const t8_forest_t forest, const t8_locidx_t ltreeid);
```
