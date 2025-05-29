```
t8_forest_vtk_write_file(forest, fileprefix, write_treeid, write_mpirank, write_level, write_element_id, write_ghosts, num_data, data)
```

Write the forest in .pvtu file format. Writes one .vtu file per process and a meta .pvtu file. This function writes ASCII files and can be used when t8code is not configure with "–with-vtk" and t8*forest*vtk*write*file*via*API is not available.

# Arguments

  * `forest`:[in] The forest.
  * `fileprefix`:[in] The prefix of the output files.
  * `write_treeid`:[in] If true, the global tree id is written for each element.
  * `write_mpirank`:[in] If true, the mpirank is written for each element.
  * `write_level`:[in] If true, the refinement level is written for each element.
  * `write_element_id`:[in] If true, the global element id is written for each element.
  * `write_ghosts`:[in] If true, each process additionally writes its ghost elements. For ghost element the treeid is -1.
  * `num_data`:[in] Number of user defined double valued data fields to write.
  * `data`:[in] Array of [`t8_vtk_data_field_t`](@ref) of length *num_data* providing the used defined per element data. If scalar and vector fields are used, all scalar fields must come first in the array.

# Returns

True if successful, false if not (process local).

### Prototype

```c
int t8_forest_vtk_write_file (t8_forest_t forest, const char *fileprefix, const int write_treeid, const int write_mpirank, const int write_level, const int write_element_id, int write_ghosts, const int num_data, t8_vtk_data_field_t *data);
```
