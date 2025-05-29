```
startassembly!(self::SysmatAssemblerFFBlock,
    elem_mat_nrows::IT,
    elem_mat_ncols::IT,
    n_elem_mats::IT,
    row_nalldofs::IT,
    col_nalldofs::IT;
    force_init = false) where {IT <: Integer}
```

Start assembly, delegate to the wrapped assembler.
