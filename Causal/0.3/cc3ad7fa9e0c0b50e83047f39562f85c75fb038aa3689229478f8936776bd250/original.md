```julia
report(simulation)

```

Records the state of the `simulation` by writing all its fields into a data file. All the fields of the `simulation` is written into file. When the file is read back, the `simulation` object is constructed back. The data file is written under the path of the `simulation`.
