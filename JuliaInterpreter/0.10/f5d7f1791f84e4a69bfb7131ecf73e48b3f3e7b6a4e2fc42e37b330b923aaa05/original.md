```
breakpoint(file, line, [condition])
```

Set a breakpoint in `file` at `line`. The argument `file` can be a filename, a partial path or absolute path. For example, `file = foo.jl` will match against all files with the name `foo.jl`, `file = src/foo.jl` will match against all paths containing `src/foo.jl`, e.g. both `Foo/src/foo.jl` and `Bar/src/foo.jl`. Absolute paths only matches against the file with that exact absolute path.
