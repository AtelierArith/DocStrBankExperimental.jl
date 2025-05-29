```
cata(lf, rf, [x])
```

Catamorphism - Return `lf()` when x is none. Otherwsie,  return `rf(x)`.  If `x` is wrapped then the result will be  wrapped.  If `x` is not provided then a curried function is returned.
