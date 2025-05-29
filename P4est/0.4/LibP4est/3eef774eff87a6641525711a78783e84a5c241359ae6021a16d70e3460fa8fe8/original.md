```
p6est_copy_ext(input, copy_data, duplicate_mpicomm)
```

Make a deep copy of a `p6est`. The connectivity is not duplicated. Copying of quadrant user data is optional. If old and new data sizes are 0, the user_data field is copied regardless. The inspect member of the copy is set to NULL.

### Parameters

  * `copy_data`:[in] If true, data are copied. If false, data_size is set to 0.
  * `duplicate_mpicomm`:[in] If true, MPI communicator is copied.

### Returns

Returns a valid `p6est` that does not depend on the input.

### Prototype

```c
p6est_t *p6est_copy_ext (p6est_t * input, int copy_data, int duplicate_mpicomm);
```
