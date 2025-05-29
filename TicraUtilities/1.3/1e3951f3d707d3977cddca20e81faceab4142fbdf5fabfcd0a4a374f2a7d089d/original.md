```
write_tepfile(filename::AbstractString, tep::TEP)
write_tepfile(filename::AbstractString, tep::Vector{TEPscatter})
```

Write a TICRA-compatible "Tabulated Electrical Properties" (TEP) file.  If `type(tep) == TEPscatter` or `type(tep) == Vector{TEPscatter}`, then the file will be written in the original format  (scattering surface) introduced by GRASP8. If `type(tep) == TEPperiodic` then the file will be written  in the newer format for periodic unit cells introduced by the QUPES program.
