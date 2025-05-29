```
fold(io::CSeis, i)
```

Return the fold of a CloudSeis frame corresponding, and where the frame is described by its index `i`.  The frame index can be either an `Int`, a `VarArg{Int}`, or a `CartesianIndex`.

# Example

```julia
io = csopen("foo.cs", "w"; axis_lengths=[10,11,12])
fold(io, 5, 6) # fold corresponding to 5th frame and 6th volume
```
