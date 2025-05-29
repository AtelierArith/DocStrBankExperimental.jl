```
t8_forest_write_vtk_ext(forest, fileprefix, write_treeid, write_mpirank, write_level, write_element_id, write_ghosts, write_curved, do_not_use_API, num_data, data)
```

### Prototype

```c
int t8_forest_write_vtk_ext (t8_forest_t forest, const char *fileprefix, const int write_treeid, const int write_mpirank, const int write_level, const int write_element_id, const int write_ghosts, const int write_curved, int do_not_use_API, const int num_data, t8_vtk_data_field_t *data);
```
