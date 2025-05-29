```
p8est_copy(input, copy_data)
```

Make a deep copy of a `p8est`. The connectivity is not duplicated. Copying of quadrant user data is optional. If old and new data sizes are 0, the user_data field is copied regardless. The inspect member of the copy is set to NULL. The revision counter of the copy is set to zero.

### Parameters

  * `copy_data`:[in] If true, data are copied. If false, data_size is set to 0.

### Returns

Returns a valid `p8est` that does not depend on the input, except for borrowing the same connectivity. Its revision counter is 0.

### Prototype

```c
p8est_t *p8est_copy (p8est_t * input, int copy_data);
```
