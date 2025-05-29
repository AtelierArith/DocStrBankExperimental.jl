```
Runic.format_file(
    inputfile::AbstractString, outputfile::AbstractString = inputfile;
    inplace::Bool=false,
)
```

Format file `inputfile` and write the formatted text to `outputfile`.

Setting the keyword argument `inplace = true` is required if `inputfile` and `outputfile` are the same file.
