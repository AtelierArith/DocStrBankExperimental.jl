```
evaluate(tsg::TasmanianSG, x)
```

evaluates the intepolant at a single points of interest and returns the result This is the accelerated version using the selected acceleration type, but it is potentially not thread safe

this should be called after the grid has been created and after values have been loaded

x: a vector with length getNumDimensions()    the entries indicate the points for evaluating the weights

output: returns vector of length getNumOutputs()         the values of the interpolant at fX
