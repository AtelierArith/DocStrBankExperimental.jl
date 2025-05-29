```
compose(t, trans1::KinematicTransformation, trans2::KinematicTransformation)
```

Return a transformation resulting from applying `trans2` and then `trans1` at time `t`.

This will likely return a `ConstantAffineMap`, but may return a more specific transformation. For example, combining two `ConstantLinearMap`s will result in a new `ConstantLinearMap`.
