```
SysmatAssemblerSparseSymm{IT, MBT, IBT} <: AbstractSysmatAssembler
```

Assembler for a **symmetric square** matrix  assembled from symmetric square matrices.

!!! note
    All fields of the datatype are private. The type is manipulated by the functions `startassembly!`, `assemble!`, and `makematrix!`.

