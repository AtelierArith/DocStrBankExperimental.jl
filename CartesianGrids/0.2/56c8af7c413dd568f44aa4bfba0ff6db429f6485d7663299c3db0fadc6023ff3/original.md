```
interpolatable_field(x,y,f::ScalarGridData)
```

Generates an interpolatable version of grid data `f`, based on coordinates in `x` and `y` (which should be in range form). The output can be called as a function with coordinate pairs as arguments.
