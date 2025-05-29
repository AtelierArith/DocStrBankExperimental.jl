```
makematrix!(self::SysmatAssemblerSparse)
```

Make a sparse matrix.

The sparse matrix is returned.

!!! note
    If `nomatrixresult` is set to true, dummy (zero) sparse matrices are returned. The entire result of the assembly is preserved in the assembler buffers. The ends of the buffers are filled with illegal (ignorable) values.


!!! note
    When the matrix is constructed (`nomatrixresult` is false), the buffers are not deallocated, and the `buffer_pointer` is set to 1. It is then possible to immediately start assembling another matrix.

