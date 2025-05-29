```
weave(source::AbstractString; kwargs...)
```

Weave an input document to output file.

## Keyword options

  * `doctype::Union{Nothing,AbstractString} = nothing`: Output document format. By default (i.e. given `nothing`), Weave will set it automatically based on file extension. You can also manually specify it; see [`list_out_formats()`](@ref) for the supported formats
  * `informat::Union{Nothing,AbstractString} = nothing`: Input document format. By default (i.e. given `nothing`), Weave will set it automatically based on file extension. You can also specify either of `"script"`, `"markdown"`, `"notebook"`, or `"noweb"`
  * `out_path::Union{Symbol,AbstractString} = :doc`: Path where the output is generated can be either of:

      * `:doc`: Path of the source document (default)
      * `:pwd`: Julia working directory
      * `"somepath"`: `String` of output directory e.g. `"~/outdir"`, or of filename e.g. `"~/outdir/outfile.tex"`
  * `args::Any = Dict()`: A runtime object that is available as `WEAVE_ARGS` while `weave`ing
  * `mod::Union{Module,Nothing} = nothing`: Module where Weave `eval`s code. You can pass a `Module` object, otherwise create an new sandbox module.
  * `fig_path::Union{Nothing,AbstractString} = nothing`: Where figures will be generated, relative to `out_path`. By default (i.e. given `nothing`), Weave will automatically create `figures` directory.
  * `fig_ext::Union{Nothing,AbstractString} = nothing`: Extension for saved figures e.g. `".pdf"`, `".png"`. Default setting depends on `doctype`
  * `cache_path::AbstractString = "cache"`: Where of cached output will be saved
  * `cache::Symbol = :off`: Controls caching of code:

      * `:off` means no caching (default)
      * `:all` caches everything
      * `:user` caches based on chunk options
      * `:refresh` runs all code chunks and save new cache
  * `template::Union{Nothing,AbstractString,Mustache.MustacheTokens} = nothing`: Template (file path) or `Mustache.MustacheTokens`s for `md2html` or `md2tex` formats
  * `css::Union{Nothing,AbstractString} = nothing`: Path of a CSS file used for md2html format
  * `highlight_theme::Union{Nothing,Type{<:Highlights.AbstractTheme}} = nothing`: Theme used for syntax highlighting (defaults to `Highlights.Themes.DefaultTheme`)
  * `pandoc_options::Vector{<:AbstractString} = String[]`: `String`s of options to pass to pandoc for `pandoc2html` and `pandoc2pdf` formats, e.g. `["--toc", "-N"]`
  * `latex_cmd::Vector{<:AbstractString} = ["xelatex", "-shell-escape", "-halt-on-error"]`: The command used to make PDF file from .tex
  * `keep_unicode::Bool = false`: If `true`, do not convert unicode characters to their respective latex representation. This is especially useful if a font and tex-engine with support for unicode characters are used

!!! note
    Run Weave from terminal and try to avoid weaving from IJulia or ESS; they tend to mess with capturing output.

