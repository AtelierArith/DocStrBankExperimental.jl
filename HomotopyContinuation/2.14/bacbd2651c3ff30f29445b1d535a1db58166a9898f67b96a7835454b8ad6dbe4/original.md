```
iterator(tracker::Tracker, x₁, t₁=1.0, t₀=0.0)
```

Prepare a tracker to make it usable as a (stateful) iterator. Use this if you want to inspect a specific path. In each iteration the tuple `(x,t)` is returned.

## Example

Assume you have `Tracker` `tracker` and you wan to track `x₁` from 1.0 to 0.25:

```julia
for (x,t) in iterator(tracker, x₁, 1.0, 0.25)
    println("x at t=$t:")
    println(x)
end
```

Note that this is a stateful iterator. You can still introspect the state of the tracker. For example to check whether the tracker was successfull (and did not terminate early due to some problem) you can do

```julia
println("Success: ", is_success(status(tracker)))
```
