```
sc_array_rewind(array, new_count)
```

Shorten an array without reallocating it.

### Parameters

  * `array`:[in,out] The element count of this array is modified.
  * `new_count`:[in] Must be less or equal than the **array**'s count. If it is less, the number of elements in the array is reduced without reallocating memory. The exception is a **new_count** of zero specified for an array that is not a view: In this case sc*array*reset is equivalent.

### Prototype

```c
void sc_array_rewind (sc_array_t * array, size_t new_count);
```
