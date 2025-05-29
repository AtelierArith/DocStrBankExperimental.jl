```
EdgeDragHandler(fun)
```

Initializes `DragHandler` for Edges. Calls function

```
fun(dragstate, idx, event, axis)
```

where `dragstate=true` during the drag and `false` at the end of the drag, the last time `fun` is triggered. `idx` is the edge index.

See [`EdgeDrag`](@ref) for a concrete implementation. ```
