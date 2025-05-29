```
TarIterator(io[, predicate])
```

Iterator over an input stream open for reading. `io` may also be pathname of an existing  tar file. The data in the stream or file must obey the `tar` file format understood by package `Tar`.

If `predicate` is given, only tar elements with matching header data are processed.

  * `String` or `Regex`: `predicate` is applied to the element names.
  * `Symbol`: it must coincide with field `type` of `Tar.Header`.
  * boolean function: it is applied to the `Tar.Header` of the elements.
  * `Tuple`: AND of all predicates contained in tuple
  * `Vector`: OR of all predicates contained in vector

Examples:

```
    io = open("/tmp/abc.tar") 
    TarIterator(io)              # all entries 
    TarIterator(io, :file)       # all entries of file type 
    TarIterator(io, "y")         # only entry with name "y" 
    TarIterator(io, r".*[.]txt") # all entries with name ending in ".txt"
    TarIterator(io, h -> h.size > 100) # only entries with data size > 100
```
