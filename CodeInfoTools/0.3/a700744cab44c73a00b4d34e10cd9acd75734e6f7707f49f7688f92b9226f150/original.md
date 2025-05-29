```
slot!(b::Builder, name::Symbol; arg = false)::Core.SlotNumber
```

Add a new `Core.SlotNumber` with associated `name::Symbol` to the in-progress `Core.CodeInfo` on the `c::Canvas` inside `b::Builder`. If `arg == false`, also performs a `pushfirst!` with a `Core.NewvarNode` for consistency in the in-progress `Core.CodeInfo`. (`arg` controls whether or not we interpreter the new slot as an argument)

`name::Symbol` must not already be associated with a `Core.SlotNumber`.
