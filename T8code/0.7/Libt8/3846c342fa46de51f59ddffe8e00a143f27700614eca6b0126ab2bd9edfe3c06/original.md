```
t8_cmesh_trees_get_part(trees, proc)
```

Return one part of a specified tree array.

# Arguments

  * `trees`:[in] The tree array to be queried
  * `proc`:[in] An index specifying the part to be returned.

# Returns

The part number *proc* of *trees*.

### Prototype

```c
t8_part_tree_t t8_cmesh_trees_get_part (const t8_cmesh_trees_t trees, const int proc);
```
