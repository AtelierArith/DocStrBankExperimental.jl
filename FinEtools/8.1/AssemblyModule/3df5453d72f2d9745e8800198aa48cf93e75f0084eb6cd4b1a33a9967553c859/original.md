```
startassembly!(self::SysmatAssemblerSparseDiag{T},
    elem_mat_nrows::IT,
    elem_mat_ncols::IT,
    n_elem_mats::IT,
    row_nalldofs::IT,
    col_nalldofs::IT;
    force_init = false
    ) where {T, IT<:Integer}
```

Start the assembly of a symmetric square diagonal matrix.

The method makes buffers for matrix assembly. It must be called before the first call to the method `assemble!`.

# Arguments

  * `elem_mat_nrows` = row dimension of the element matrix;
  * `elem_mat_ncols` = column dimension of the element matrix;
  * `n_elem_mats` = number of element matrices;
  * `row_nalldofs`= The total number of rows as a tuple;
  * `col_nalldofs`= The total number of columns as a tuple.

The values stored in the buffers are initially undefined!

# Returns

  * `self`: the modified assembler.
