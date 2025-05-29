```
MMCIFDict(filepath; gzip=false)
MMCIFDict(io; gzip=false)
MMCIFDict()
```

A macromolecular Crystallographic Information File (mmCIF) dictionary.

Can be accessed using similar functions to a standard `Dict`. Keys are field names as a `String` and values are always `Vector{String}`, even for multiple components or numerical data. To directly access the underlying dictionary of `MMCIFDict` `d`, use `d.dict`. Call `MMCIFDict` with a filepath or stream to read the dictionary from that source. The keyword argument `gzip` (default `false`) determines if the input is gzipped.
