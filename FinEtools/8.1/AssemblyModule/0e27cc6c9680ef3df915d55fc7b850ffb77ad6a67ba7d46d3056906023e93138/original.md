```
SysmatAssemblerSparseHRZLumpingSymm{IT, MBT, IBT} <: AbstractSysmatAssembler
```

Assembler for a **symmetric lumped square** matrix  assembled from  **symmetric square** matrices.

Reference: A note on mass lumping and related processes in the finite element method, E. Hinton, T. Rock, O. C. Zienkiewicz, Earthquake Engineering & Structural Dynamics, volume 4, number 3, 245–249, 1976.

!!! note
    All fields of the datatype are private. The type is manipulated by the functions `startassembly!`, `assemble!`, and `makematrix!`.


!!! note
    This assembler can compute and assemble diagonalized mass matrices. However, if the meaning of the entries of the mass matrix  differs (translation versus rotation), the mass matrices will not be computed correctly. Put bluntly: it can only be used for homogeneous mass matrices, all translation degrees of freedom, for instance.

