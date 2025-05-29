```
readmeta(io::IO)
```

Read an Object File out from an `IOStream`, guessing at the type of object within the stream by calling `readmeta(io, T)` for each `T` within `ObjTypes`, and returning the first that does not throw a `MagicMismatch`.
