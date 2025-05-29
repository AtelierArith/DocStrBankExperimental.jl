```
startassembly!(self::SysvecAssembler, ndofs_row)
```

Start assembly.

The method makes the buffer for the vector assembly. It must be called before the first call to the method assemble.

`ndofs_row`= Total number of degrees of freedom.

# Returns

  * `self`: the modified assembler.
