```
sc_array_copy(dest, src)
```

Copy the contents of one array into another. Both arrays must have equal element sizes. The source array may be a view. We use memcpy (3): If the two arrays overlap, results are undefined.

### Parameters

  * `dest`:[in] Array (not a view) will be resized and get new data.
  * `src`:[in] Array used as source of new data, will not be changed.

### Prototype

```c
void sc_array_copy (sc_array_t * dest, sc_array_t * src);
```
