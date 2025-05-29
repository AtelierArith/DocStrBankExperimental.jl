```
D = stats(D::GMTdataset, cols=0) -> GMTdataset
```

Return descriptive statistics for a dataset `GMTdataset` where each row represents the statistics for each column.

If `cols` is a column name, either as a String or a Symbol, or a column number, only the statistics for that column are returned.
