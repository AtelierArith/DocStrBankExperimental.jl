evaluateThreadSafe(tsg::TasmanianSG, x)         evaluates the intepolant at a single points of interest and         returns the result         This is the thread safe version, but it does not use         acceleration of any type

```
    this should be called after the grid has been created and after
    values have been loaded

    x: vector with length dimensions
       the entries indicate the points for evaluating the weights

    output: returns a vector of length getNumOutputs
            the values of the interpolant at x
```
