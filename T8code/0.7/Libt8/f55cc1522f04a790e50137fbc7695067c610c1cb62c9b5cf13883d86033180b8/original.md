```
t8_forest_get_num_ghosts(forest)
```

Return the number of ghost elements of a forest.

# Arguments

  * `forest`:[in] The forest.

# Returns

The number of ghost elements stored in the ghost structure of *forest*. 0 if no ghosts were constructed.

# See also

[`t8_forest_set_ghost`](@ref) *forest* must be committed before calling this function.

### Prototype

```c
t8_locidx_t t8_forest_get_num_ghosts (const t8_forest_t forest);
```
