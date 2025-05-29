```
AnalysisMethod(
    conctable::AbstractDataTable, 
    signaltable::Union{AbstractDataTable, Nothing}, 
    signal, 
    pointlevel = Int[]; 
    signal = :area, 
    rel_sig = :relative_signal, 
    est_conc = :estimated_concentration, 
    true_conc = :true_concentration, 
    kwargs...
)
```

Convenient contructors for `AnalysisMethod` which make constructing a `Table` optional.

`signal` data type for quantification. `levelname` is the column name for `pointlevel`. See `AnalysisMethod` for details of other arguments.

# Keyword arguments

  * `rel_sig`: key name of relative signal.
  * `est_conc`: key name of estimated concentration.
  * `true_conc`: key name of true concentration.
  * `acc`: key name of accuracy.
  * Other keyword arguments will be columns in `analytetable`; when `analyte`, `isd` and `calibration` are not provided, it will use analyte in `conctable`.
