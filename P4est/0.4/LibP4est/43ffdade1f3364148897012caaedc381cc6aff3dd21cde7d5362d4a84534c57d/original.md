```
sc_array_move_part(dest, dest_offset, src, src_offset, count)
```

Copy part of one array into another using memmove (3). Both arrays must have equal element sizes. Either array may be a view. The destination array must be large enough. We use memmove (3): The two arrays may overlap.

### Parameters

  * `dest`:[in] Array will be written into. Its element count must be at least **dest_offset** + **count**.
  * `dest_offset`:[in] First index in **dest** array to be overwritten. As every index, it refers to elements, not bytes.
  * `src`:[in] Array will be read from. Its element count must be at least **src_offset** + **count**.
  * `src_offset`:[in] First index in **src** array to be used. As every index, it refers to elements, not bytes.
  * `count`:[in] Number of entries copied.

### Prototype

```c
void sc_array_move_part (sc_array_t * dest, size_t dest_offset, sc_array_t * src, size_t src_offset, size_t count);
```
