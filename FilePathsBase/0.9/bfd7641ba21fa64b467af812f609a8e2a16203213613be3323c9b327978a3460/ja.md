```
  cwd() -> SystemPath
```

現在の作業ディレクトリを取得します。

# 例

```julia-repl
julia> cwd()
p"/home/JuliaUser"

julia> cd(p"/home/JuliaUser/Projects/julia")

julia> cwd()
p"/home/JuliaUser/Projects/julia"
```
