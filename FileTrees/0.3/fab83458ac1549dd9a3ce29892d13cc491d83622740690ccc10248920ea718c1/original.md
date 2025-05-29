```
reducevalues(f, t::FileTree; associative=true, init=nothing)
```

Use `f` to combine values in the tree.

  * `associative=true` assumes `f` can be applied in an associative way
  * `init` keyword argument will be returned if the file tree is empty. if `init` is not provided, reduce over an empty tree will cause an error to be thrown
