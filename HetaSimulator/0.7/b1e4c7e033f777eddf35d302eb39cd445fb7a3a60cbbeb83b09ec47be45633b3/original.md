```
read_measurements(filepath::String, sheet=1; kwargs...)
```

Reads table file with measurements to `DataFrame`

Arguments:

  * `filepath` : path to table file. Supports ".csv" and ".xlsx" files
  * `sheet` : number of sheet in case of ".xlsx" file. Default is `1`
  * kwargs... : other arguments supported by `CSV.File` or `XLSX.readtable`
