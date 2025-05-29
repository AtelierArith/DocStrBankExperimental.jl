```
startassembly!(self::SysvecAssembler{T}, ndofs_row::FInt) where {T<:Number}
```

Start assembly.

The method makes the buffer for the vector assembly. It must be called before the first call to the method assemble.

  * `elem_mat_nmatrices` = number of element matrices expected to be processed during the assembly.
  * `ndofs_row`= Total number of degrees of freedom.

# Returns

  * `self`: the modified assembler.
