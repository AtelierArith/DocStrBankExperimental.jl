```
v = getindex(ds::AbstractDataset, varname::SymbolOrString)
```

Return the variable `varname` in the dataset `ds` as a `CFVariable`. The following CF convention are honored when the variable is indexed:

  * `_FillValue` or `missing_value` (which can be a list) will be returned as `missing`.
  * `scale_factor` and `add_offset` are applied (output = `scale_factor` * `data_in_file` +  `add_offset`)
  * time variables (recognized by the units attribute and possibly the calendar attribute) are returned usually as `DateTime` object. Note that `CFTime.DateTimeAllLeap`, `CFTime.DateTimeNoLeap` and `CF.TimeDateTime360Day` cannot be converted to the proleptic gregorian calendar used in julia and are returned as such. (See [`CFTime.jl`](https://github.com/JuliaGeo/CFTime.jl) for more information about those date types.) If a calendar is defined but not among the ones specified in the CF convention, then the data in the file is not converted into a date structure.

A call `getindex(ds, varname)` is usually written as `ds[varname]`.

If variable represents a cell boundary, the attributes `calendar` and `units` of the related variables are used, if they are not specified. For example:

```
dimensions:
  time = UNLIMITED; // (5 currently)
  nv = 2;
variables:
  double time(time);
    time:long_name = "time";
    time:units = "hours since 1998-04-019 06:00:00";
    time:bounds = "time_bnds";
  double time_bnds(time,nv);
```

In this case, the variable `time_bnds` uses the units and calendar of `time` because both variables are related thought the bounds attribute following the CF conventions.

See also [`cfvariable(ds, varname)`](@ref).
