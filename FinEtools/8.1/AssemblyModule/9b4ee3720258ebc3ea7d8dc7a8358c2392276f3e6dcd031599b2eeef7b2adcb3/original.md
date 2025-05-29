```
SysmatAssemblerSparse{IT, MBT, IBT} <: AbstractSysmatAssembler
```

Type for assembling a sparse global matrix from elementwise matrices.

!!! note
    All fields of the datatype are private. The type is manipulated by the functions `startassembly!`, `assemble!`, and `makematrix!`.

