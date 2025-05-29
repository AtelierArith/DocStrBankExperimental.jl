```
p6est_copy(input, copy_data)
```

Make a deep copy of a `p6est`. The connectivity is not duplicated. Copying of quadrant user data is optional. If old and new data sizes are 0, the user_data field is copied regardless.

### Parameters

  * `copy_data`:[in] If true, data are copied. If false, data_size is set to 0.

### Returns

Returns a valid `p6est` that does not depend on the input.

### Prototype

```c
p6est_t *p6est_copy (p6est_t * input, int copy_data);
```
