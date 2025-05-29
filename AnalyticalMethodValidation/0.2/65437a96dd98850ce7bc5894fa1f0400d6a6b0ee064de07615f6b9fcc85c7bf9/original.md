```
ap_report(at::AnalysisTable; 
            id = r"Pre.*_(.*)_.*", 
            type = :accuracy, 
            pct = true, 
            colanalyte = :Analyte,
            colstats = :Stats,
            colday = :Day,
            collevel = :Level
        )
```

Compute accuracy and precision. A `NamedTuple` is returned with two elements: `daily` is a `DataFrame` containing accuracy and standard deviation for each day, and `summary` is a `DataFrame` containing overall accuracy, repeatability and reproducibility. 

# Arguments

  * `at`: `AnalysisTable`.
  * `id`: `Regex` identifier for the AP experiment samples. The day and concentration level is captured in the identifier; the order can be set by `order`.
  * `order`: a string for setting the order of captured values from `id`; D is day; L is concentration level.
  * `type`: data type for calculation.
  * `pct`: whether converting ratio data into percentage (*100).
  * `colanalyte`: column name of analytes.
  * `colstats`: column name of statistics.
  * `colday`: column name of validation day.
  * `collevel`: column name of level.
