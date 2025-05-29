```julia
save(
    filename,
    td;
    include_preamble,
    latex_engine,
    buildflags,
    dpi,
    showing_ide
)

```

Save the argument (either [`TikzDocument`](@ref), or some other type which is wrapped in one automatically, eg [`TikzPicture`](@ref), [`Axis`](@ref), or [`Plot`](@ref)) to `filename`, guessing the format from the file extension. Keywords specify options, some specific to some output formats.

`pgfsave` is an alias which is exported.
