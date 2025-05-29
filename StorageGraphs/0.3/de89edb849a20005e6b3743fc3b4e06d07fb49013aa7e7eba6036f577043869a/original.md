```
function walkdep(g, dep::Pair; stopcond=(g,v)->false)
```

Walk along the dependency chain, but only on already existing paths, and return the last node and the compatible paths.
