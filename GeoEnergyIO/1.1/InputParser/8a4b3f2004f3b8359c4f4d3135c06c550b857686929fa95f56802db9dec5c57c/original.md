```
parse_grdecl_file("mygrid.grdecl"; actnum_path = missing, kwarg...)
```

Parse a GRDECL file separately from the full input file. Note that the GRID section does not contain units - passing the `input_units` keyword is therefore highly recommended.

# Keyword arguments

  * `actnum_path=missing`: Path to ACTNUM file, if this is not included in the main file.
  * `units=:si`: Units to use for return values. Requires `input_units` to be set.
  * `input_units=nothing`: The units the file is given in.
  * `verbose=false`: Toggle verbosity.
  * `extra_paths`: List of extra paths to parse as a part of grid section, ex: `["PORO.inc", "PERM.inc"]`.
