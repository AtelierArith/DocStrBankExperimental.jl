```
clip()
```

Establish a new clipping region by intersecting the current clipping region with the current path and then clearing the current path.

An existing clipping region is enforced through and after a `gsave()`-`grestore()` block, but a clipping region set inside a `gsave()`-`grestore()` block is lost after `grestore()`. [?]
