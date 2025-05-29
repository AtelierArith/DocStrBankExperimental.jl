```
_add_output(from, to)
```

adds `to` as an output of `from`.

User code should never call `_add_output` directly, only through `connect`.  Users might specialize `_add_output` if implementing a node that needs to specialize how it stores its outputs.
