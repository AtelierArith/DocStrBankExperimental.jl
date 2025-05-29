```
NoOp <: Augmentor.AffineOperation
```

Identity transformation that does not do anything with the given image, but instead passes it along unchanged (without copying).

Usually used in combination with [`Either`](@ref) to denote a "branch" that does not perform any computation.
