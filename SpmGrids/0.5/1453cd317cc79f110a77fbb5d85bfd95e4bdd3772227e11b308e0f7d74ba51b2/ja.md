```
channel_names(grid::SpmGrid, skip_bwd=true)::Array{String}
```

`grid`内のすべてのチャネル名を返します。`skip_bwd`が`true`の場合、bwd方向のチャネル名は返されません。
