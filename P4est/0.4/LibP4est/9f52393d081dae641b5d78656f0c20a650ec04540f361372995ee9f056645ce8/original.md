```
sc_array_truncate(array)
```

Sets the array count to zero, but does not free elements. Not allowed for views.

!!! note
    This is intended to allow an [`sc_array`](@ref) to be used as a reusable buffer, where the "high water mark" of the buffer is preserved, so that O(log (max n)) reallocs occur over the life of the buffer.


### Parameters

  * `array`:[in,out] Array structure to be truncated.

### Prototype

```c
void sc_array_truncate (sc_array_t * array);
```
