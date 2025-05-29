```
plot_plane(data::NamedTuple, ax::Any, ax_cb::Any, backend::Module; kwargs...)::Nothing
```

NamedTuple `data` から Axis `ax` に平面をプロットします。カラーバーも `ax_cb` にプロットされます。Makie バックエンドを指定する必要があり、追加のキーワード引数を提供できます。
