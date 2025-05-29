```
function allocate_aca_memory(
    ::Type{K}, maxrows::I, maxcolumns::I; maxrank=40
) where {I, K}
```

Preallocation of sorage for the ACA.

# Arguments

  * `::Type{K}`: Type of matrix entries.
  * `maxrows::I`: Number of rows.
  * `maxcolumns::I`: Number of columns.

# Optional Arguments

  * `maxrank=40`: Maximum rank for the ACA. The ACA stops of more rows/columns are used for

the approximation.
