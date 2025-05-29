```
t8_cmesh_trees_ghost_attribute_size(ghost)
```

Return the total size of all attributes stored at a specified ghost.

# Arguments

  * `ghost`:[in] A ghost structure.

# Returns

The total size (in bytes) of the attributes of *ghost*.

### Prototype

```c
size_t t8_cmesh_trees_ghost_attribute_size (t8_cghost_t ghost);
```
