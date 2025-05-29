```
t8_offset_first_tree_to_entry(first_tree, shared)
```

Given the global tree id of the first local tree of a process and the flag whether it is shared or not, compute the entry in the offset array. This entry is the first_tree if it is not shared and -first_tree - 1 if it is shared.

# Arguments

  * `first_tree`:[in] The global tree id of a process's first tree.
  * `shared`:[in] 0 if *first_tree* is not shared with a smaller rank, 1 if it is.

# Returns

The entry that represents the process in an offset array. *first_tree* if *shared* == 0 - *first_tree* - 1 if *shared* != 0

### Prototype

```c
t8_gloidx_t t8_offset_first_tree_to_entry (const t8_gloidx_t first_tree, const int shared);
```
