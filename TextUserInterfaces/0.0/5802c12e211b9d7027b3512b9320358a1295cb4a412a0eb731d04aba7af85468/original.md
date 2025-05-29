```
function set_focus_chain(wins::Window...; new_focus_id::Integer = 1)
```

Set the focus chain, *i.e.* the ordered list of windows that can receive the focus. The keyword `new_focus_id` can be set to specify which element is currently focused in the new chain.
