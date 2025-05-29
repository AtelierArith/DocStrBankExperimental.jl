```
write_stationfile(stationfile::AbstractString, stdat::Station)
write_stationfile(stationfile::AbstractString, stdat::AbstractVector{Station})
```

Write a Ticra POS4-compatible optimization station file.  Here, when `stdat` is a vector, its elements are the partitions in the station file. 
