```
read_stationfile(stationfile) -> Vector{Station}
```

Read the contents of a Ticra optimization station file. The returned value is a vector of length `npart`, where `npart` is the number of partitions in the file.
