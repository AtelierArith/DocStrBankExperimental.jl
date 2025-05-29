```
mapvalues(f, x::FileTree)
```

(See `load` to load values into nodes of a tree.)

Apply `f` to the value of all nodes in `x` which have a value. Returns a new tree where every value is replaced with the result of applying `f`.

`f` may return `NoValue()` to cause no value to be associated with a node.
