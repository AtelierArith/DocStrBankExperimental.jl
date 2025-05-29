```
setDomainTransform!(tsg::TasmanianSG, Transform::VecOrMat)
```

sets the lower and upper bound for each dimension

Note: gauss-laguerre and gauss-hermite rules are defined on       unbounded domain, in which case  this sets the       shift and scale parameters, consult the manual

Transform: a matrix of size dimension X 2            transform specifies the lower and upper bound            of the domain in each direction.

```
       For gauss-laguerre and gauss-hermite grids, the
       transform gives the a and b parameters of the
       weights
        exp(-b (x - a))
        exp(-b (x - a)^2)
```
