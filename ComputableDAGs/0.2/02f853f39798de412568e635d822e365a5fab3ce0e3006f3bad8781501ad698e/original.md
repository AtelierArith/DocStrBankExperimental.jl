```
partners(node::Node, set::Set{Node})
```

Alternative version to [`partners(node::Node)`](@ref), avoiding allocation of a new set. Works on the given set and returns `nothing`.
