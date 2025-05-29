```
MemoryKind
```

Trait object used to signal if values of a type is semantically equal to their own `MemoryView`. If so, `MemoryKind(T)` should return an instance of `IsMemory`, else `NotMemory()`. The default implementation `MemoryKind(::Type)` returns `NotMemory()`.

If `MemoryKind(T) isa IsMemory{M}`, the following must hold:

1. `M` is a concrete subtype of `MemoryView`. To obtain `M` from an `m::IsMemory{M}`,  use `inner(m)`.
2. `MemoryView(T)` is a valid instance of `M`.
3. `MemoryView(x) == x` for all instances `x::T`

Some objects can be turned into `MemoryView` without being `IsMemory`. For example, `MemoryView(::String)` returns a valid `MemoryView` even though `MemoryKind(String) === NotMemory()`. This is because strings have different semantics than memory views - the latter is a dense `AbstractArray` while strings are not, and so the fourth requirement `MemoryView(x::String) == x` does not hold.

See also: [`MemoryView`](@ref)
