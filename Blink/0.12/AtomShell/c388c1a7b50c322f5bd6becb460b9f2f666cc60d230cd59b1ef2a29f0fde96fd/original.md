```
active(win::Window)::Bool
active(connection)::Bool
```

Indicates whether the specified `Window` (or `Page`, `shell`, or other internal component) is currently "active," meaning it has an open connection to its Electron component.

```julia-repl
julia> w = Window();

julia> active(w)
true

julia> close(w)

julia> active(w)
false
```
