```
p8est_save_ext(filename, p8est_, save_data, save_partition)
```

Save the complete connectivity/`p8est` data to disk. This is a collective operation that all MPI processes need to call. All processes write into the same file, so the filename given needs to be identical over all parallel invocations. See [`p8est_load_ext`](@ref) for information on the autopartition parameter.

!!! note
    Aborts on file errors.


### Parameters

  * `filename`:[in] Name of the file to write.
  * `p8est`:[in] Valid forest structure.
  * `save_data`:[in] If true, the element data is saved. Otherwise, a data size of 0 is saved.
  * `save_partition`:[in] If false, save file as if 1 core was used. If true, save core count and partition. Advantage: Partition can be recovered on loading with same mpisize and autopartition false. Disadvantage: Makes the file depend on mpisize. Either way the file can be loaded with autopartition true.

### Prototype

```c
void p8est_save_ext (const char *filename, p8est_t * p8est, int save_data, int save_partition);
```
