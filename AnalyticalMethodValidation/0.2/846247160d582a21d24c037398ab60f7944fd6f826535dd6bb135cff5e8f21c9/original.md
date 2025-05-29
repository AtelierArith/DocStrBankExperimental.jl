```
sample_report(at::AnalysisTable; id = r"Sample_(\d*).*", type = :estimated_concentration, colanalyte = :Analyte)
```

Compute mean of sample data.

# Arguments

  * `at`: `AnalysisTable`.
  * `id`: `Regex` identifier for the QC samples.
  * `type`: data type for calculation.
  * `colanalyte`: column name of analytes.
