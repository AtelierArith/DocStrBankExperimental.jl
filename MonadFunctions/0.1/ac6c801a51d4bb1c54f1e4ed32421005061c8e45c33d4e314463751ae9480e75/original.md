```
fmap(f, [x])
fmap(f...)
```

Map function `f` over value `x`.  If `x` is wrapped then the result will be wrapped as well.  If `x` is not provided then a curried  function is returned.
