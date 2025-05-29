```
sym2asym(cut::Cut) -> cut2
```

Convert a symmetrical (in θ) `Cut` to a new asymmetrical `Cut`.  An asymmetrical cut begins at θ = 0, while a symmetrical cut covers equal extents of negative and  positive angles.  If the input `cut` is already asymmetrical, then return a copy of  this input as the output.
