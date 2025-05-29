```
p8est_connectivity_save(filename, connectivity)
```

Save a connectivity structure to disk.

### Parameters

  * `filename`:[in] Name of the file to write.
  * `connectivity`:[in] Valid connectivity structure.

### Returns

Returns 0 on success, nonzero on file error.

### Prototype

```c
int p8est_connectivity_save (const char *filename, p8est_connectivity_t * connectivity);
```
