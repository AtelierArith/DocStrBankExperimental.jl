```
PriorityChannel{T}(sz::Int)
```

Constructs a `PriorityChannel` with an internal buffer that can hold a maximum of `sz` objects of type `T`, each assigned an real-valued priority (low number = higher priority). [`put!`](@ref) calls on a full channel block until an object is removed with [`take!`](@ref).

`PriorityChannel(0)` constructs an unbuffered channel. `put!` blocks until a matching `take!` is called. And vice-versa.

Other constructors:

  * `PriorityChannel(Inf)`: equivalent to `PriorityChannel{Any,Int}(typemax(Int))`
  * `PriorityChannel(sz)`: equivalent to `PriorityChannel{Any,Int}(sz)`
