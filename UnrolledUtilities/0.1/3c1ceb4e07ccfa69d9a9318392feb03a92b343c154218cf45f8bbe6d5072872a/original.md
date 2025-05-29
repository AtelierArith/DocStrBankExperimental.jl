```
StaticOneTo(N)
```

A lazy and statically sized analogue of `Base.OneTo(N)`.

This iterator can only store the integers from 1 to `N`, so its `output_type_for_promotion` is `NoOutputType()`. An efficient method is provided for `unrolled_take`, but no other unrolled functions can use `StaticOneTo`s as output types.
