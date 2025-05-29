```
loadNeededPoints!(tsg::TasmanianSG, vals::Array{Float64})
```

loads the values of the target function at the needed points if there are no needed points, this reset the currently loaded values

vals: an array with dimensions outputs X getNumNeeded()        each column corresponds to the values of the outputs at       the corresponding needed point. The order and leading       dimension must match the points obtained from       getNeededPoints()
