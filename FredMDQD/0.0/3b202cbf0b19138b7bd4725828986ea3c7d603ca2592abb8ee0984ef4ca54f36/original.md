```
FredQD(path::String)
FredQD(d::Date)
FredQD()
```

Load Fred QD data. 

## Arguments

  * `path::String`: Path to a manually downloaded version of Fred QD.
  * `d::Date`: Date of a vintage.

## Details

  * If no arguments are provided, the most recent version of Fred QD will be downloaded.
  * If a `d::Date` is provided, the Fred QD vintage corresponding to the date will be downloaded.
  * If a `path::String` is provided, then the Fred QD file at the `path` will be loaded.

## Notes

  * Fred QD data is compiled by Michael W. McCracken at the Federal Reserve Bank of St. Louis. For more information check out the official website at https://research.stlouisfed.org/econ/mccracken/fred-databases/
