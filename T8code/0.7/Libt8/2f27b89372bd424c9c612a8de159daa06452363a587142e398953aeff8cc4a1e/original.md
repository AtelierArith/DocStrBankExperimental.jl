```
t8_forest_partition_data(forest_from, forest_to, data_in, data_out)
```

Re-Partition an array accordingly to a partitioned forest.

!!! note
    *data_in* has to be of size equal to the number of local elements of *forest_from* *data_out* has to be already allocated and has to be of size equal to the number of local elements of *forest_to*.


# Arguments

  * `forest_form`:[in] The forest before the partitioning step.
  * `forest_to`:[in] The partitioned forest of *forest_from*.
  * `data_in`:[in] A pointer to an [`sc_array_t`](@ref) holding data (one value per element) accordingly to *forest_from*.
  * `data_out`:[in,out] A pointer to an already allocated [`sc_array_t`](@ref) capable of holding data accordingly to *forest_to*.

### Prototype

```c
void t8_forest_partition_data (t8_forest_t forest_from, t8_forest_t forest_to, const sc_array_t *data_in, sc_array_t *data_out);
```
