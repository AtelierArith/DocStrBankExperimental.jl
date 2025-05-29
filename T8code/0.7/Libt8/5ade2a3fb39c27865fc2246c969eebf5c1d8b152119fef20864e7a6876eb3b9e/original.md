```
t8_forest_get_first_local_element_id(forest)
```

Compute the global index of the first local element of a forest. This function is collective.

# Arguments

  * `forest`:[in] A committed forest, whose first element's index is computed.

# Returns

The global index of *forest*'s first local element. Forest must be committed when calling this function. This function is collective and must be called on each process.

### Prototype

```c
t8_gloidx_t t8_forest_get_first_local_element_id (t8_forest_t forest);
```
