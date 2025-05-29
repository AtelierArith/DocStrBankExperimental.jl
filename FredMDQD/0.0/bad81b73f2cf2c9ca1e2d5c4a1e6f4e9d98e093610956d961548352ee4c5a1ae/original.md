```
FredMD(path::String)
FredMD(d::Date)
FredMD()
```

Load Fred MD data. 

## Arguments

  * `path::String`: Path to a manually downloaded version of Fred MD.
  * `d::Date`: Date of a vintage.

## Details

  * If no arguments are provided, the most recent version of Fred MD will be downloaded.
  * If a `d::Date` is provided, the Fred MD vintage corresponding to the date will be downloaded.
  * If a `path::String` is provided, then the Fred MD file at the `path` will be loaded.

## Notes

  * Fred MD data is compiled by Michael W. McCracken at the Federal Reserve Bank of St. Louis. For more information check out the official website at https://research.stlouisfed.org/econ/mccracken/fred-databases/
