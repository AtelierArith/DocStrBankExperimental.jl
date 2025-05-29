```
sdfilereader(file::IO)
sdfilereader(path::AbstractString)
```

Read SDFile data from input stream (or a file path as a string) and return a lazy iterator that yields molecule objects.

`sdfilereader` does not stop and raise errors when an erroneous or incompatible SDFile block is read but produces an error message and yields an empty molecule. If this behavior is not desirable, you can use the customized supplier function instead of default supplier `nohaltsupplier`
