```
xyz2h5(xyz_xyz::String, xyz_h5::String, flight::Symbol;
       lines::Vector        = [()],
       lines_type::Symbol   = :exclude,
       tt_sort::Bool        = true,
       downsample_160::Bool = true,
       return_data::Bool    = false)
```

Convert SGL flight data file from .xyz to HDF5.

  * Valid for SGL flights:

      * `:Flt1001`
      * `:Flt1002`
      * `:Flt1003`
      * `:Flt1004_1005`
      * `:Flt1004`
      * `:Flt1005`
      * `:Flt1006`
      * `:Flt1007`
      * `:Flt1008`
      * `:Flt1009`
      * `:Flt1001_160Hz`
      * `:Flt1002_160Hz`
      * `:Flt2001_2017`

May take 1+ hr for 1+ GB files. For reference, a 1.23 GB file took 46.8 min to process using a 64 GB MacBook Pro.

**Arguments:**

  * `xyz_xyz`:        path/name of flight data .xyz file (`.xyz` extension optional)
  * `xyz_h5`:         path/name of flight data HDF5 file to save (`.h5` extension optional)
  * `flight`:         flight name (e.g., `:Flt1001`)
  * `lines`:          (optional) selected line number(s) to ONLY include or exclude, must be a vector of 3-element (`line`,`start_time`,`end_time`) tuple(s)
  * `lines_type`:     (optional) whether to ONLY `:include` (i.e., to generate testing data) or `:exclude` (i.e., to generate training data) `lines`
  * `tt_sort`:        (optional) if true, sort data by time (instead of line)
  * `downsample_160`: (optional) if true, downsample 160 Hz data to 10 Hz (only for 160 Hz data files)
  * `return_data`:    (optional) if true, return `data` instead of creating `xyz_h5`

**Returns:**

  * `data`: if `return_data = true`, internal data matrix
