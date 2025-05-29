```
ReadStatColumns
```

A set of data columns for efficient data collection with `ReadStat`.

A concrete array type is specified for holding each possible type of data values defined in `ReadStat`. Data columns containing the same type of data values are stored in the same `Vector` with a concrete element type. A vector of tuples is used to locate the `Vector` where a data column is stored and its index within that `Vector`.
