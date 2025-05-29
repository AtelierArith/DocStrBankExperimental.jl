```julia
compile_directory(; ...)
compile_directory(dir; source, archive)

```

Compile `joinpath(dir, source)` using `Literate.markdown`, put the source, manifest, and project files in an archive, add it as a footer.

`dir` defaults to `pwd()`.
