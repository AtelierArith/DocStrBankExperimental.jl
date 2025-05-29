```
build_notebooks(
    bopts::BuildOptions,
    [files,]
    oopts::OutputOptions=OutputOptions();
    session=ServerSession()
)
```

`dir`内のPlutoノートブック`files`をビルドします。ここで、`files`はオプションです。`files`を渡さない場合、`dir`内のすべてのPlutoノートブックがビルドされます。

# 例

```
julia> dir = joinpath(homedir(), "my_project", "notebooks");

julia> bopts = BuildOptions(dir);

julia> oopts = OutputOptions(; append_build_context=true);

julia> files = ["pi.jl", "math.jl"];

julia> build_notebooks(bopts, files, oopts);
```
