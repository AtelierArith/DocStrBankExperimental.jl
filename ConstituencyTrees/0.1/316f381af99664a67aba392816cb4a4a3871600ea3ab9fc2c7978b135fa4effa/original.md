```
chomsky_normal_form(tree, factor=RightFactored(), labelf)
```

Convert a tree into chomsky normal form.

# Arguments

  * `tree`: the constituency tree to convert
  * `factor=RightFactored()`: can be `LeftFactored()` or `RightFactored()`
  * `labelf`: function (called like `labelf(tree, children)`)

# Returns

  * a tree of the same type as its argument
