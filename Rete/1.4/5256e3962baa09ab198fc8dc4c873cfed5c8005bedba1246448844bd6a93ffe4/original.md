```
_add_input(from, to)
```

adds `from` as an input to `to`.

User code should never call `_add_input` directly, only through `connect`.  Users might specialize `_add_input` if implementing a node that needs to specialize how it stores its inputs.
