```
t8_forest_vtk_write_file_via_API(forest, fileprefix, write_treeid, write_mpirank, write_level, write_element_id, curved_flag, write_ghosts, num_data, data)
```

Write the forest in .pvtu file format. Writes one .vtu file per process and a meta .pvtu file. This function uses the vtk library. t8code must be configured with "–with-vtk" in order to use it. Currently does not support pyramid elements.

!!! note
    If t8code was not configured with vtk, use t8*forest*vtk*write*file


# Arguments

  * `forest`:[in] The forest.
  * `fileprefix`:[in] The prefix of the output files. The meta file will be named *fileprefix*.pvtu .
  * `write_treeid`:[in] If true, the global tree id is written for each element.
  * `write_mpirank`:[in] If true, the mpirank is written for each element.
  * `write_level`:[in] If true, the refinement level is written for each element.
  * `write_element_id`:[in] If true, the global element id is written for each element.
  * `curved_flag`:[in] If true, write the elements as curved element types from vtk.
  * `write_ghosts`:[in] If true, write out ghost elements as well.
  * `num_data`:[in] Number of user defined double valued data fields to write.
  * `data`:[in] Array of [`t8_vtk_data_field_t`](@ref) of length *num_data* providing the user defined per element data. If scalar and vector fields are used, all scalar fields must come first in the array.

# Returns

True if successful, false if not (process local).

### Prototype

```c
int t8_forest_vtk_write_file_via_API (t8_forest_t forest, const char *fileprefix, const int write_treeid, const int write_mpirank, const int write_level, const int write_element_id, const int curved_flag, const int write_ghosts, const int num_data, t8_vtk_data_field_t *data);
```
