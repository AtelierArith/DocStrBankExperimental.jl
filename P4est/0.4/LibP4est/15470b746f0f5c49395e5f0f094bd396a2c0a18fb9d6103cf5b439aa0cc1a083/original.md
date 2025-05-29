```
sc_array_destroy_null(parray)
```

Destroys an array structure and sets the pointer to NULL.

### Parameters

  * `parray`:[in,out] Pointer to address of array to be destroyed. On output, *parray is NULL.

### Prototype

```c
void sc_array_destroy_null (sc_array_t ** parray);
```
