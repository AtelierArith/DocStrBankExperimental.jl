```
qc_report(at::AnalysisTable;
            id = r"PooledQC", 
            type = :estimated_concentration, 
            pct = true,
            stats = [mean, std, pct ? rsd_pct : rsd], 
            names = ["Mean", "Standard Deviation", "Relative Standard Deviation" * (pct ? "(%)" : "")], 
            colanalyte = :Analyte,
            colstats = :Stats
        )
```

Compute statistics of QC data.

# Arguments

  * `at`: `AnalysisTable`.
  * `id`: `Regex` identifier for the QC samples.
  * `pct`: whether converting ratio data into percentage (*100).
  * `type`: data type for calculation.
  * `stats`: statistics functions.
  * `names`: names of statistics. When `nothing` is given, `stats` is served as `names`.
  * `colanalyte`: column name of analytes.
  * `colstats`: column name of statistics.
