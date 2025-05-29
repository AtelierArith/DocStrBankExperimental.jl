```
sc_array_memset(array, c)
```

Run memset on the array storage. We pass the character to memset unchanged. Thus, care must be taken when setting values below -1 or above 127, just as with standard memset (3).

### Parameters

  * `array`:[in,out] This array's storage will be overwritten.
  * `c`:[in] Character to overwrite every byte with.

### Prototype

```c
void sc_array_memset (sc_array_t * array, int c);
```
