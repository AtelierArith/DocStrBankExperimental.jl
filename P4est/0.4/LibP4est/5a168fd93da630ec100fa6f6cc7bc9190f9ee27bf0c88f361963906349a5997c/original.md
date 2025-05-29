```
sc_array_split(array, offsets, num_types, type_fn, data)
```

Compute the offsets of groups of enumerable types in an array.

### Parameters

  * `array`:[in] Array that is sorted in ascending order by type. If k indexes *array*, then 0 <= *type_fn* (*array*, k, *data*) < *num_types*.
  * `offsets`:[in,out] An initialized array of type size_t that is resized to *num_types* + 1 entries. The indices j of *array* that contain objects of type k are *offsets*[k] <= j < *offsets*[k + 1]. If there are no objects of type k, then *offsets*[k] = *offset*[k + 1].
  * `num_types`:[in] The number of possible types of objects in *array*.
  * `type_fn`:[in] Returns the type of an object in the array.
  * `data`:[in] Arbitrary user data passed to *type_fn*.

### Prototype

```c
void sc_array_split (sc_array_t * array, sc_array_t * offsets, size_t num_types, sc_array_type_t type_fn, void *data);
```
