```
plot_cube(data::NamedTuple, ax::Any, ax_cb::Any, backend::Module; kwargs...)::Nothing
```

NamedTuple `data` から Axis `ax` に立方体をプロットします。色バーも `ax_cb` にプロットされます。Makie バックエンドを指定する必要があり、追加のキーワード引数を提供できます。
