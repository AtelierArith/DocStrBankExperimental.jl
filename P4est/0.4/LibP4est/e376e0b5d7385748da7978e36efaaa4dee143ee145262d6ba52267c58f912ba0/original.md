```
sc_vtk_write_compressed(vtkfile, numeric_data, byte_length)
```

This function writes numeric binary data in VTK compressed format.

### Parameters

  * `vtkfile`: Stream opened for writing.
  * `numeric_data`: A pointer to a numeric data array.
  * `byte_length`: The length of the data array in bytes.

### Returns

Returns 0 on success, -1 on file error.

### Prototype

```c
int sc_vtk_write_compressed (FILE * vtkfile, char *numeric_data, size_t byte_length);
```
