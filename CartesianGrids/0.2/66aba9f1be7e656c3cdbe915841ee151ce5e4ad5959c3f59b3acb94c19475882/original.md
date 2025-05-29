```
interpolatable_field(xu,yu,xv,yv,f::EdgeData/NodePair)
```

Generates an interpolatable version of grid data `f`, based on coordinates in `xu`, `yu`, `xv`, `yv` (which should be in range form). The output can be called as a function with coordinate pairs as arguments.
