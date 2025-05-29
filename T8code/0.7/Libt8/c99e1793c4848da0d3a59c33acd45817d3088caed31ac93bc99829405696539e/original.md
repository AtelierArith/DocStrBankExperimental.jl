```
t8_forest_partition_create_tree_offsets(forest)
```

Create the array tree offsets of a partitioned forest. This arrays stores at position p the global id of the first tree of this process. Or if this tree is shared, it stores -(global_id) - 1.

# Arguments

  * `forest`:[in,out] The forest. *forest* must be committed before calling this function.

### Prototype

```c
void t8_forest_partition_create_tree_offsets (t8_forest_t forest);
```
