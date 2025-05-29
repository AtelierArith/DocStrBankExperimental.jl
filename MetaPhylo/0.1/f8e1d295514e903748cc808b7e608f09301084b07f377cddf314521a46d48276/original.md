```
swapchildren!(tree::Tree, idx::Integer, newchildren)
```

Swap the child indices of the specified `idx` node to the given `newchildren`. The elements of children and `newchildren` must be match. Return `false` if swapping fails; true otherwise.
