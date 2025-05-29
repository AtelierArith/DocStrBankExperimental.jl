```
File(filename::String, blafilename::String)
```

Read a fixed width file, using the specs from blafile. Returns an object implementing the Tables interface. 

If the file starts with the 3 byte BOM for utf-8, it will be skipped. The line-ending is determined based on the first line. If the file uses a mixed line ending, the data will not be read correctly.

# Examples

```julia-repl
julia> using DataFrames, FWFTables
julia> df = DataFrame(FWFTables.File("data.asc", "spec.bla"))
```
