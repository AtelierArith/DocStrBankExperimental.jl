```
addparg!(fi::FuncInfo, name::Symbol [, index::Integer])
```

Adds a new argument to `FuncInfo` with the specified `name`, and insert it to the position arguments.  If `index` is not provided, insert it to the last non-vararg position. Returns the new `SlotNumber`.  Equivalent to `addarg!` + `insertparg!`.
