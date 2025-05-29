```
startassembly!(self::SysmatAssemblerSparseSymm{T},
    elem_mat_nrows::IT,
    elem_mat_ncols::IT,
    n_elem_mats::IT,
    row_nalldofs::IT,
    col_nalldofs::IT;
    force_init = false
    ) where {T, IT<:Integer}
```

Start the assembly of a global matrix.

The method makes buffers for matrix assembly. It must be called before the first call to the method `assemble!`.

# Arguments

  * `elem_mat_nrows` = row dimension of the element matrix;
  * `elem_mat_ncols` = column dimension of the element matrix;
  * `n_elem_mats` = number of element matrices;
  * `row_nalldofs`= The total number of rows as a tuple;
  * `col_nalldofs`= The total number of columns as a tuple.

If the `buffer_pointer` field of the assembler is 0, which is the case after that assembler was created, the buffers are resized appropriately given the dimensions on input. Otherwise, the buffers are left completely untouched. The `buffer_pointer` is set to the beginning of the buffer, namely 1.

# Returns

  * `self`: the modified assembler.

!!! note
    The buffers may be automatically resized if more numbers are assembled then initially intended. However, this operation will not necessarily be efficient and fast.


!!! note
    The buffers are initially not filled with anything meaningful. After the assembly, only the `(self._buffer_pointer - 1)` entries are meaningful numbers. Beware!

