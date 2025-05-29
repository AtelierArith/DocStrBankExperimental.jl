```
EdgeDragHandler(fun)
```

エッジのための `DragHandler` を初期化します。関数を呼び出します

```
fun(dragstate, idx, event, axis)
```

ここで、`dragstate=true` はドラッグ中、`false` はドラッグの最後で、`fun` が最後にトリガーされるときです。`idx` はエッジのインデックスです。

具体的な実装については [`EdgeDrag`](@ref) を参照してください。 ```
