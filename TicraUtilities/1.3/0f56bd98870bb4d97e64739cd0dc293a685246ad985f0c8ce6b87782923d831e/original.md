```
read_tepfile(filename::AbstractString)
```

Read a TICRA-compatible "Tabulated Electrical Properties" (TEP) file.  The file may be in either the original format (scattering surface) originated by GRASP8 or the newer format for periodic unit cells created by the QUPES program.  The return value depends on the type of TEP file encountered:

  * Old-style scattering surface: For a TEP file containing data for a single frequency, the return value will be a scalar object of type `TEPscatter`.  If the file contains data for multiple frequencies, the return value will be an object of type `Vector{TEPscatter}`, with one element for each frequency.
  * New-style periodic unit cell: The return value will be an object of type `TEPperiodic`.  Note that the file may not contain swept geometrical parameters.
