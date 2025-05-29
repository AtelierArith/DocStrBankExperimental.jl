```
trixi_load_cell_averages(data::Ptr{Cdouble}, simstate_handle::Cint)::Cvoid
```

Return cell averaged solution state.

Cell averaged values for each cell and each primitive variable are stored in a contiguous array, where cell values for the first variable appear first and values for the other variables subsequently (structure-of-arrays layout).

The given array has to be of correct size and memory has to be allocated beforehand.
