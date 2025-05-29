```julia
struct Canvas
    defs::Vector{Tuple{Int, Int}}
    code::Vector{Any}
    codelocs::Vector{Int32}
end
Canvas() = Canvas(Tuple{Int, Int}[], [], Int32[])
```

A `Vector`-like abstraction for `Core` code nodes.

Properties to keep in mind:

1. Insertion anywhere is slow.
2. Pushing to beginning is slow.
3. Pushing to end is fast.
4. Deletion is fast.
5. Accessing elements is fast.
6. Setting elements is fast.

Thus, if you build up a `Canvas` instance incrementally, everything should be fast.
