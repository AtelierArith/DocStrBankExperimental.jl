```
build_notebooks(
    bopts::BuildOptions,
    [files,]
    oopts::OutputOptions=OutputOptions();
    session=ServerSession()
)
```

Build Pluto notebook `files` in `dir`. Here, `files` is optional. When not passing `files`, then all Pluto notebooks in `dir` will be built.

# Example

```
julia> dir = joinpath(homedir(), "my_project", "notebooks");

julia> bopts = BuildOptions(dir);

julia> oopts = OutputOptions(; append_build_context=true);

julia> files = ["pi.jl", "math.jl"];

julia> build_notebooks(bopts, files, oopts);
```
