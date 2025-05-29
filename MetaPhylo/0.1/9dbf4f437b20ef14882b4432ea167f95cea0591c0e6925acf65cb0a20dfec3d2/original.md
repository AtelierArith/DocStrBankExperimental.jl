```
swap!(tree::Tree, idx::Integer, old_new::Pair{<:Integer, <:Integer})
```

Swap the two child elements of the specified `idx` node. The `old` and `new` in `old_new` must be child of `idx` node. Return `ture` if swapping fails; true otherwise.
