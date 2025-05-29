```
sc_vtk_write_binary(vtkfile, numeric_data, byte_length)
```

This function writes numeric binary data in VTK base64 encoding.

### Parameters

  * `vtkfile`: Stream opened for writing.
  * `numeric_data`: A pointer to a numeric data array.
  * `byte_length`: The length of the data array in bytes.

### Returns

Returns 0 on success, -1 on file error.

### Prototype

```c
int sc_vtk_write_binary (FILE * vtkfile, char *numeric_data, size_t byte_length);
```
