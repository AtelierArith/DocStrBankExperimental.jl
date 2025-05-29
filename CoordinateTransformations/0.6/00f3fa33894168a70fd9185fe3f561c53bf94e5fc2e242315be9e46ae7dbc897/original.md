```
compose(trans1, trans2)
trans1 ∘ trans2
```

Take two transformations and create a new transformation that is equivalent to successively applying `trans2` to the coordinate, and then `trans1`. By default will create a `ComposedTransformation`, however this method can be overloaded for efficiency (e.g. two affine transformations naturally compose to a single affine transformation).
