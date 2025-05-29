```
as(T, args...)
```

Shorthand for constructing transformations with image in `T`. `args` determines or modifies behavior, details depend on `T`.

Not all transformations have an `as` method, some just have direct constructors. See `methods(as)` for a list.

# Examples

```julia
as(Real, -∞, 1)          # transform a real number to (-∞, 1)
as(Array, 10, 2)         # reshape 20 real numbers to a 10x2 matrix
as(Array, as𝕀, 10)       # transform 10 real numbers to (0, 1)
as((a = asℝ₊, b = as𝕀)) # transform 2 real numbers a NamedTuple, with a > 0, 0 < b < 1
as(SArray{1,2,3}, as𝕀)  # transform to a static array of positive numbers
```
