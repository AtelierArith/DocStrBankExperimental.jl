```
create_project_here()
create_project_here(include_examples=false)
```

現在の作業ディレクトリにMicroTrackerプロジェクトのフォルダ構造を作成します。

`include_examples`がfalseの場合、サンプルの粒子データとビデオは含まれません。

# 例

```julia-repl
julia> pwd()
"~/tutorial"

julia> create_project_here()
[ Info: New MicroTracker project created in ~/tutorial
```
