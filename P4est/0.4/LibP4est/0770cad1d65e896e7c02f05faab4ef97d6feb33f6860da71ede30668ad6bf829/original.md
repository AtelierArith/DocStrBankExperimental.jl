```
p6est_save(filename, p6est_, save_data)
```

Save the complete connectivity/`p6est` data to disk. This is a collective

operation that all MPI processes need to call. All processes write into the same file, so the filename given needs to be identical over all parallel invocations.

!!! note
    Aborts on file errors.


### Parameters

  * `filename`:[in] Name of the file to write.
  * `p6est`:[in] Valid forest structure.
  * `save_data`:[in] If true, the element data is saved. Otherwise, a data size of 0 is saved.

### Prototype

```c
void p6est_save (const char *filename, p6est_t * p6est, int save_data);
```
