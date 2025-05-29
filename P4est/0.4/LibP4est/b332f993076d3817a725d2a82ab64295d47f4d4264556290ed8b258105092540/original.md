```
sc_strcopy(dest, size, src)
```

Provide a string copy function.

### Parameters

  * `dest`:[out] Buffer of length at least *size*. On output, not touched if NULL or *size* == 0.
  * `size`:[in] Allocation length of *dest*.
  * `src`:[in] Null-terminated string.

### Returns

Equivalent to sc_snprintf (dest, size, "s", src).

### Prototype

```c
void sc_strcopy (char *dest, size_t size, const char *src);
```
