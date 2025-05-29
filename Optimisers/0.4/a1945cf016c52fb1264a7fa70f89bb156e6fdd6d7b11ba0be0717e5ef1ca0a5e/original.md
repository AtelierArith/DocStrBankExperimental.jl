```
Optimisers.thaw!(tree)
```

The reverse of [`freeze!`](@ref Optimisers.freeze!). Applies to all parameters, mutating every `Leaf(rule, state, frozen = true)` to `Leaf(rule, state, frozen = false)`.
