```
SysmatAssemblerSparseDiag{T<:Number} <: AbstractSysmatAssembler
```

Assembler for a **symmetric square diagonal** matrix  assembled from symmetric square diagonal matrices.

Warning: off-diagonal elements of the elementwise matrices will be ignored during assembly!

!!! note
    All fields of the datatype are private. The type is manipulated by the functions `startassembly!`, `assemble!`, and `makematrix!`.

