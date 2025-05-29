```
p4est_connectivity_load(filename, bytes)
```

Load a connectivity structure from disk.

### Parameters

  * `filename`:[in] Name of the file to read.
  * `bytes`:[in,out] Size in bytes of connectivity on disk or NULL.

### Returns

Returns valid connectivity, or NULL on file error.

### Prototype

```c
p4est_connectivity_t *p4est_connectivity_load (const char *filename, size_t *bytes);
```
