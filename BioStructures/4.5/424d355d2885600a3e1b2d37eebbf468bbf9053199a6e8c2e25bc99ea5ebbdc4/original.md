```
MMTFDict(filepath; gzip=false)
MMTFDict(io; gzip=false)
MMTFDict()
```

A Macromolecular Transmission Format (MMTF) dictionary.

Use of the dictionary requires the MMTF.jl package to be imported. Can be accessed using similar functions to a standard `Dict`. Keys are field names as a `String` and values are various types. To directly access the underlying dictionary of `MMTFDict` `d`, use `d.dict`. Call `MMTFDict` with a filepath or stream to read the dictionary from that source. The keyword argument `gzip` (default `false`) determines if the file is gzipped.
