```
stability_report(at::AnalysisTable; 
                    day0 = r"S.*_(.*)_.*", 
                    stored = r"S.*_(.*)_(.*)_(.*)_.*", 
                    order = "CDL", 
                    type = :accuracy, 
                    pct = true,                             
                    colanalyte = :Analyte,
                    colstats = :Stats,
                    colcondition = :Condition,
                    colday = :Day,
                    collevel = :Level,
                    isaccuracy = true
                )
```

Compute stability. A `NamedTuple` is returned with three elements: `day0` is a `DataFrame` conataing day0 samples, `stored` is a `DataFrame` conataing stored samples, and `stored_over_day0` is `stored` divided by `day0`. 

if `day0` is not available, both `day0` and `stored_over_day0` are empty `DataFrame`s.

# Arguments

  * `at`: `AnalysisTable`.
  * `day0`: `Regex` identifier for day0 samples. The concentration level is captured in the identifier.
  * `stored`: `Regex` identifier for stored samples. The storage condition, concentration level, and storage days are captured in the identifier; the order can be set by `order`.
  * `order`: a string for setting the order of captured values from `id`; C is storage condition; D is storage days; L is concentration level
  * `type`: data type for calculation.
  * `pct`: whether converting ratio data into percentage (*100).
  * `colanalyte`: column name of analytes.
  * `colstats`: column name of statistics.
  * `colcondition`: column name of storage condition.
  * `colday`: column name of validation day.
  * `collevel`: column name of level.
  * `isaccuracy`: whether the input data is accuracy.
