```
p4est_save(filename, p4est_, save_data)
```

Save the complete connectivity/`p4est` data to disk.

This is a collective operation that all MPI processes need to call. All processes write into the same file, so the filename given needs to be identical over all parallel invocations.

By default, we write the current processor count and partition into the file header. This makes the file depend on mpisize. For changing this see [`p4est_save_ext`](@ref)() in p4est_extended.h.

The revision counter is not saved to the file, since that would make files different that come from different revisions but store the same mesh.

!!! note
    Aborts on file errors.


!!! note
    If `p4est` is not configured to use MPI-IO, some processes return from this function before the file is complete, in which case immediate read-access to the file may require a call to `sc_MPI_Barrier`.


### Parameters

  * `filename`:[in] Name of the file to write.
  * `p4est`:[in] Valid forest structure.
  * `save_data`:[in] If true, the element data is saved. Otherwise, a data size of 0 is saved.

### Prototype

```c
void p4est_save (const char *filename, p4est_t * p4est, int save_data);
```
