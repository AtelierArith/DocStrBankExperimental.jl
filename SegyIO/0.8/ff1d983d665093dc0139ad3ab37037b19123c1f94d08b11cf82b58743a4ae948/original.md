```
scan_file(file::String, keys::Array{String, 1}, blocksize::Int;
          chunksize::Int = CHUNKSIZE,
          verbosity::Int = 1)
```

Scan `file` for header fields in `keys`, and return a SeisCon object containing the metadata summaries in `blocksize` groups of traces. Load `chunksize` MB of `file` into memory at a time.

If the number of traces in `file` are not divisible by `blocksize`, the last block will summarize the remaining traces.

`verbosity` set to 0 silences updates on the current file being scanned.

# Example

```
s = scan_file('testdata.segy', ["SourceX", "SourceY"], 300)
```
