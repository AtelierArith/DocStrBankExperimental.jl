```
importcsv(filepath::String; delimiter=',', header=false, comment = "Imported from csv file", savelog = true, kwargs...)
```

Load data from a CSV file (two/three columns, comma separated by default but delimiter can be specified in the `delimiter` keyword argument). 

The function can be used to construct either a RheoTimeData instance or a RheoFreqData instance, depending on the parameters provided or column names;the function detects whether time or frequency has been included and proceeds accordingly. For oscillatory data, all three columns (Gp, Gpp, Frequency) must be provided. For regular viscoelastic data only time, or time-stress, or time-strain or time-stress-strain data can be provided.

Column can be specified in the csv file by providing their values or header name (case insensitive) as keyword parameters. 

`importcsv("filename.csv", time=1, strain=2, stress=3)` loads a `RheoTimeData` from a csv file with time in the first column, strain in the second, and stress in the third.

`importcsv("filename.csv", omega="Frequency", Gp="Storage", Gpp="Loss")` would detect the column numbers by reading the headers on the csv file.

If no information is provided, it would try to detect columns from header names, expecting standard names. Some of the recognised keywords are `time`, `stress`, `strain`, `frequency`, `storage modulus`, `loss modulus`.

If the csv file contains headers, but it is prefered to indicate columns by their numbers rather than header strings, the keyword `header` must be set to `true`.
