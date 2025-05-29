```
readplist(stream::IO) -> Dict
readplist(filename::AbstractString) -> Dict
```

Read a NeXTSTEP style PList from file named `filename`, or from an `IO` stream object you have opened previously. This could be from a file, a string or a socket. In each case you get a dictionary back.
