```
timeline(r)
```

Generate `RheoTimeData` struct with only the time data based on the range provided.

# Example:

`timeline(0:0.1:10)` returns a RheoTimeData with only time data, with the following series: [0.  0.1   0.2  ...  9.9  10].
