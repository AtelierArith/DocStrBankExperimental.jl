```
t8_forest_get_local_num_elements(forest)
```

Return the number of process local elements in the forest.

# Arguments

  * `forest`:[in] A forest.

# Returns

The number of elements on this process in *forest*. *forest* must be committed before calling this function.

### Prototype

```c
t8_locidx_t t8_forest_get_local_num_elements (const t8_forest_t forest);
```
