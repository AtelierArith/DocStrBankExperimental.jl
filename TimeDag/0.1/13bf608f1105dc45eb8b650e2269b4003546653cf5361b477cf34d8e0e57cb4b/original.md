```
history(x::Node{T}, window::Int) -> Node{Vector{T}}
```

Create a node whose values represent the last `window` values seen in `x`.

Each value will be vector of length `window`, and the result will only start ticking once `window` values have been seen. The vector value contains time-ordered observations, with the most recent observation last.
