```
MemoryView{T, M} <: DenseVector{T}
```

View into a `Memory{T}`. Construct from memory-backed values `x` with `MemoryView(x)`.

`MemoryView`s are guaranteed to point to contiguous, valid CPU memory, except where they have size zero.

The parameter `M` controls the mutability of the memory view, and may be `Mutable` or `Immutable`, corresponding to the the aliases `MutableMemoryView{T}` and `ImmutableMemoryView{T}`.

See also: `MemoryKind`

# Examples

```jldoctest
julia> v = view([1, 2, 3, 4], 2:3);

julia> mem = MemoryView(v)
2-element MutableMemoryView{Int64}:
 2
 3

julia> MemoryView(codeunits("abc")) isa ImmutableMemoryView{UInt8}
true
```

# Extended help

New types `T` which are backed by dense memory should implement:

  * `MemoryView(x::T)` to construct a memory view from `x`. This should  always return a `MutableMemoryView` when the memory of `x` is mutable.
  * `MemoryKind(x::T)`, if `T` is semantically equal to its own memory view. Examples of this include `Vector`, `Memory`, and `Base.CodeUnits{UInt8, String}`. If so, `x == MemoryView(x)` should hold.

If `MemoryView(x)` is implemented, then `ImmutableMemoryView(x)` will automatically work, even if `MemoryView(x)` returns a mutable view.

It is not possible to mutate memory though an `ImmutableMemoryView`, but the existence of the view does not protect the same memory from being mutated though another variable.

The precise memory layout of the data in a `MemoryView` follows that of `Memory`. This includes the fact that some elements in the array, such as  `String`s, may be stored as pointers, and [isbits Union optimisations](https://docs.julialang.org/en/v1/devdocs/isbitsunionarrays/).
