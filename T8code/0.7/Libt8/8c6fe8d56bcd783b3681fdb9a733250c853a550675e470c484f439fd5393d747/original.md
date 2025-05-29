```
t8_forest_get_eclass(forest, ltreeid)
```

Return the element class of a forest local tree.

# Arguments

  * `forest`:[in] The forest.
  * `ltreeid`:[in] The local id of a tree in *forest*.

# Returns

The element class of the tree *ltreeid*. *forest* must be committed before calling this function.

### Prototype

```c
t8_eclass_t t8_forest_get_eclass (const t8_forest_t forest, const t8_locidx_t ltreeid);
```
