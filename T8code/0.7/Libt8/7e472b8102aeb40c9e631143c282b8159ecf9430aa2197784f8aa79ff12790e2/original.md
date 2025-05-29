```
t8_forest_get_global_num_elements(forest)
```

Return the number of global elements in the forest.

# Arguments

  * `forest`:[in] A forest.

# Returns

The number of elements (summed over all processes) in *forest*. *forest* must be committed before calling this function.

### Prototype

```c
t8_gloidx_t t8_forest_get_global_num_elements (const t8_forest_t forest);
```
