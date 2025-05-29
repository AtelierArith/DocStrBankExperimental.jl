```
asym2sym(cut::Cut) -> cut2
```

Convert an asymmetrical (in θ) `Cut` to a new symmetrical `Cut`.  An asymmetrical cut begins at θ = 0, while a symmetrical cut covers equal extents of negative and  positive angles.  If the input `cut` is already symmetrical, then return a copy of  this input as the output.
