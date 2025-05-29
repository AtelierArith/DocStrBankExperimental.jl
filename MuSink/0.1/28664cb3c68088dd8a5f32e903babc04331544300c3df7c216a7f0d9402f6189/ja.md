```
transport_window(plan::Coupling, i, j; conditional = false)
transport_window(plan::Coupling, (i, j); conditional = false)

transport_window(ws::Workspace, a, b, i, j; conditional = false)
transport_window(ws::Workspace, a, b, (i, j); conditional = false)
```

[`transport`](@ref)と同様ですが、ピクセル位置`(i, j)`の周りに半径`reach`のウィンドウを返します。

!!! note
    この関数は隣接ノード間のカップリングにのみ実装されています。

