```
add_measurements!(data::Dict, meas_file::String; actual_meas::Bool = false, seed::Int=0)
```

Add measurement data from separate CSV file to the PowerModelsDistribution data dictionary. To fully understand how this function works, it is recommended to first read the documentation section that describes the CSV measurement file format.

# Arguments

  * `data`: MATHEMATICAL data dictionary in a format usable with PowerModelsDistribution
  * `meas_file`: path to and name of file with measurement data
  * `actual_meas`: default is false. When applied to non-normal distributions,       the effect is overruled to that of `true`. For normal distributions, the following applies:

      * `false`: the "par*1" in meas*file are not actual measurements, but, e.g.,   error-free powerflow results. Then, a fake measurement is built, extracting   a value with an error from the given normal distribution.
      * `true`: the "par*1" values in meas*file are actual measurement values,   and the "par_2" are the σs of the measurements' distributions. These are   directly used as input of the state estimator without further processing.
      * if a "parse" column is present in the CSV file, the `true` or `false` is associated   to each individual row (i.e., measurement), and overrules whatever the actual*meas   input of add*measurements!() itself is.
  * `seed`: random seed value to make the results reproducible and explore different   Monte Carlo scenarios when sampling measurement with errors from a probability distribution.
