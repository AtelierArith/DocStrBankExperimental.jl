```
EDF.File(io::IO)
```

Return an `EDF.File` instance that wraps the given `io`, as well as EDF-formatted file, signal, and annotation headers that are read from `io`. This constructor only reads headers, not the subsequent sample data; to read the subsequent sample data from `io` into the returned `EDF.File`, call `EDF.read!(file)`.
