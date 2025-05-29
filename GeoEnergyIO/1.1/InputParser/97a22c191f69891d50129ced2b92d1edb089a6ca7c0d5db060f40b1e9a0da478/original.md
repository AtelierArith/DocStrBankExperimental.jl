```
region = get_data_file_cell_region(data, t::Symbol; active = nothing)
satnum = get_data_file_cell_region(data, :satnum)
pvtnum = get_data_file_cell_region(data, :pvtnum, active = 1:10)
```

Get the region indicator of some type for each cell of the domain stored in `data` (the output from [`parse_data_file`](@ref)). The optional keyword argument `active` can be used to extract the values for a subset of cells.

`t` should be one of the following:

  * `:satnum` (saturation function region)
  * `:pvtnum` (PVT function region)
  * `:eqlnum` (equilibriation region)
  * `:eosnum` (equation-of-state region)
