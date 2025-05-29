```
ThickPlate(length,thick,n,[λ=1.0]) <: Body
```

Construct a flat plate with length `length` and thickness `thick`, with `n` points distributed along one side.

The optional parameter `λ` distributes the points differently. Values between `0.0` and `1.0` are accepted.

Alternatively, the shape can be specified with a target point spacing in place of `n`.
