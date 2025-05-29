```
tangle(source::AbstractString; kwargs...)
```

Tangle source code from input document to .jl file.

## Keyword options

  * `informat::Union{Nothing,AbstractString} = nothing`: Input document format. By default (i.e. given `nothing`), Weave will set it automatically based on file extension. You can also specify either of `"script"`, `"markdown"`, `"notebook"`, or `"noweb"`
  * `out_path::Union{Symbol,AbstractString} = :doc`: Path where the output is generated can be either of:

      * `:doc`: Path of the source document (default)
      * `:pwd`: Julia working directory
      * `"somepath"`: `String` of output directory e.g. `"~/outdir"`, or of filename e.g. `"~/outdir/outfile.tex"`
