```
Register{Reg, T}
```

Represents a register named `Reg` (a `Symbol`), holding data of type `T`, which is expected to be a bitfield from FieldFlags.jl.

!!! warn "Internal fields"
    Internally, this is represented as a `Ptr{T}`, pointing to the memory mapped register at the given address. This is an implementation detail and may change at any time.

