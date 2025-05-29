```
inline_const!(ir::IRCode)
```

This performs constant propagation on `IRCode` so after the constant propagation during abstract interpretation, we can force inline constant values in `IRCode`.
