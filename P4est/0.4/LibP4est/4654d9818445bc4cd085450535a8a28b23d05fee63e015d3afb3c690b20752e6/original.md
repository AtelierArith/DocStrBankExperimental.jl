```
sc_array_copy_into(dest, dest_offset, src)
```

Copy the contents of one array into some portion of another. Both arrays must have equal element sizes. Either array may be a view. The destination array must be large enough. We use memcpy (3): If the two arrays overlap, results are undefined.

### Parameters

  * `dest`:[in] Array will be written into. Its element count must be at least **dest_offset** + **src**->elem_count.
  * `dest_offset`:[in] First index in **dest** array to be overwritten. As every index, it refers to elements, not bytes.
  * `src`:[in] Array used as source of new data, will not be changed.

### Prototype

```c
void sc_array_copy_into (sc_array_t * dest, size_t dest_offset, sc_array_t * src);
```
