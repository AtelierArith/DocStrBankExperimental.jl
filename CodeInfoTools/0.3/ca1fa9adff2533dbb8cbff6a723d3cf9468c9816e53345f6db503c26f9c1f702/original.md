```
get_slot(ci::CodeInfo, s::Symbol)
```

Get the `Core.Compiler.SlotNumber` associated with the `s::Symbol` in `ci::CodeInfo`. If there is no associated `Core.Compiler.SlotNumber`, returns `nothing`.
