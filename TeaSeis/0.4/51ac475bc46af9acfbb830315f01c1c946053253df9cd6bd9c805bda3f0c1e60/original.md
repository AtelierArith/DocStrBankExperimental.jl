```
fold(io, idx...)
```

Compute the fold of a frame where idx is the frame/volume/hypercube indices.  For example, `fold(jsopen("file.js"),1)` for a 3D dataset, `fold(jsopen("file.js",1,2))` for a 4D dataset, and `fold(jsopen("file.js"),1,2,3)` for a 5D dataset.
