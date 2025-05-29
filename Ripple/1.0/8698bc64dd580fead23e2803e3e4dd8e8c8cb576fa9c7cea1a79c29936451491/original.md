```
function read_nev(fname::String)
```

Read the NEV file `fname` and return a [`NEVFile`](@ref).

This method is still under contruction. Several of the extended headers and packet types were not implemented yet.

This method is based on the NEV 2.2 file format as specified by Ripple from their [documentation](https://rippleneuro.s3-us-west-2.amazonaws.com/downloads/documentation/NEVspec2_2_v07.pdf)
