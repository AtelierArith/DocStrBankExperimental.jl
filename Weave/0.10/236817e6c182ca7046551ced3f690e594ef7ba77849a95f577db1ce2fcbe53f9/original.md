```
convert_doc(infile::AbstractString, outfile::AbstractString; outformat::Union{Nothing,AbstractString} = nothing)
```

Convert Weave documents between different formats

  * `infile`: Path of the input document
  * `outfile`: Path of the output document
  * `outformat = nothing`: Output document format (optional). By default (i.e. given `nothing`) Weave will try to automatically detect it from the `outfile`'s extension. You can also specify either of `"script"`, `"markdown"`, `"notebook"`, or `"noweb"`
