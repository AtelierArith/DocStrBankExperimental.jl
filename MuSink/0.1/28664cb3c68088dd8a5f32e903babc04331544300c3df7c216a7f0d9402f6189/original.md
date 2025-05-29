```
transport_window(plan::Coupling, i, j; conditional = false)
transport_window(plan::Coupling, (i, j); conditional = false)

transport_window(ws::Workspace, a, b, i, j; conditional = false)
transport_window(ws::Workspace, a, b, (i, j); conditional = false)
```

Like [`transport`](@ref) but returns a window of radius `reach` around the pixel posiiton `(i, j)`.

!!! note
    This function is only implemented for couplings between neighboring nodes.

