```
ClosedCurve(f; tol=<default>)
ClosedCurve(f,a,b; tol=<default)
```

Construct a `ClosedCurve` object from the complex-valued function `point` accepting an argument in the interval [0,1]. The constructor checks whether `f(0)≈f(1)` to tolerance `tol`. If `a` and `b` are given, they are the limits of the parameter in the call to the supplied `f`. However, the resulting object will be defined on [0,1], which is internally scaled to [a,b].

```
ClosedCurve(f,df[,a,b]; tol=<default>)
```

Construct a closed curve with point location and tangent given by the complex-valued functions `f` and `df`, respectively, optionally with given limits on the parameter.
