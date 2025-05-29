```
evaluateHierarchicalFunctions(tsg::TasmanianSG, x)
```

evaluates the hierarchical functions at a set of points in the domain and return a matrix with the result

x: a matrix of dimensions tsg.dimensions by getNumPoints(tsg)     the columns indicate the points for evaluating the weights

output: returns a matrix of dimensions          shape == [x.shape[0], getNumPoints()]         the values of the basis functions at the points
