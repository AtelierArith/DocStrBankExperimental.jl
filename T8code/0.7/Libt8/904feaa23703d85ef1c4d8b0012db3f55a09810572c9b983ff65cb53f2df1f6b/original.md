```
t8_forest_ghost_exchange_data(forest, element_data)
```

Exchange ghost information of user defined element data.

!!! note
    This function is collective and hence must be called by all processes in the forest's MPI Communicator.


# Arguments

  * `forest`:[in] The forest. Must be committed.
  * `element_data`:[in] An array of length num_local_elements + num_ghosts storing one value for each local element and ghost in *forest*. After calling this function the entries for the ghost elements are update with the entries in the *element_data* array of the corresponding owning process.

### Prototype

```c
void t8_forest_ghost_exchange_data (t8_forest_t forest, sc_array_t *element_data);
```
