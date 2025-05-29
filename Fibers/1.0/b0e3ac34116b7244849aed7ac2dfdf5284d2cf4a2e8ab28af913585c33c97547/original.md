```
xfm_compose(xfm1::Xform{T}, xfm2::Xform{T}...)
```

Compose two transforms and return a new `Xform` structure

Note that the last argument of this function is the "innermost" transform, i.e., the one that would be applied first to the input data, and the first argument is the "outermost" transform, i.e., the one that would be applied last: output = `xfm1` * `xfm2` * ... * input
