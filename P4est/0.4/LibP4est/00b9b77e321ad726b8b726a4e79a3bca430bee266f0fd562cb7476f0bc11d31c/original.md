```
sc_array_is_equal(array, other)
```

Check whether two arrays have equal size, count, and content. Either array may be a view. Both arrays will not be changed.

### Parameters

  * `array`:[in] One array to be compared.
  * `other`:[in] A second array to be compared.

### Returns

True if array and other are equal, false otherwise.

### Prototype

```c
int sc_array_is_equal (sc_array_t * array, sc_array_t * other);
```
