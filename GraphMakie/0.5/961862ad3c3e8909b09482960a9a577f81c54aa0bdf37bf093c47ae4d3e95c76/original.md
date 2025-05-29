```
beziersegments(paths::Vector{AbstractPath})
beziersegments!(sc, paths::Vector{AbstractPath})
```

Recipe to draw bezier pathes. Each path will be descritized and ploted with a separate `lines` plot. Scalar attributes will be used for all subplots. If you provide vector attributs of same length als the pathes the i-th `lines` subplot will see the i-th attribute.

TODO: Beziersegments plot won't work if the number of pathes changes.
