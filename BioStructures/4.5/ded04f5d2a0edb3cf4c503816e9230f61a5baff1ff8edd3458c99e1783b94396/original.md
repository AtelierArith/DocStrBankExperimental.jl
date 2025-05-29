```
readmultimmcif(filepath; gzip=false)
readmultimmcif(io; gzip=false)
```

Read multiple `MMCIFDict`s from a filepath or stream. Each `MMCIFDict` in the returned `Dict{String, MMCIFDict}` corresponds to an mmCIF data block from the input. An example of such a file is the chemical component dictionary from the Protein Data Bank. The keyword argument `gzip` (default `false`) determines if the input is gzipped.
