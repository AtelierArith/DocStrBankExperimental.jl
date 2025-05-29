```
t8_cmesh_vtk_write_file(cmesh, fileprefix)
```

Write the cmesh in .pvtu file format. Writes one .vtu file per process and a meta .pvtu file. This function writes ASCII files and can be used when t8code is not configure with "–with-vtk" and t8*cmesh*vtk*write*file*via*API is not available.

# Arguments

  * `cmesh`:[in] The cmesh
  * `fileprefix`:[in] The prefix of the output files

# Returns

int

### Prototype

```c
int t8_cmesh_vtk_write_file (t8_cmesh_t cmesh, const char *fileprefix);
```
