```
scan_file(file::String, keys::Array{String, 1};
          chunksize::Int = CHUNKSIZE,
          verbosity::Int = 1)
```

Scan `file` for header fields in `keys`, and return a SeisCon object containing the metadata summaries in single-source groups of traces. Load `chunksize` MB of `file` into memory at a time.

# Example

```
s = scan_file('testdata.segy', ["SourceX", "SourceY"])
```
