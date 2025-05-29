```
add_edge!(model::ABM{<:GraphSpace},  args...; kwargs...)
```

グラフに新しいエッジ（2つの位置間の関係）を追加します。操作が成功した場合は、真のブール値を返します。

`args` と `kwargs` は、基盤となるグラフタイプに作用する `add_edge!` ディスパッチに直接渡されます。
