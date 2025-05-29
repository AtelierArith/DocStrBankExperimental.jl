```
addin!(asm,global,block,ibr,ibc,factor=1.)
```

Add a sparse `block` into a large `out` sparse matrix, at block-row and -column `ibr` and `ibc`.      Use [`prepare`](@ref) to allocate memory for `global` and build the assembler `asm`.
