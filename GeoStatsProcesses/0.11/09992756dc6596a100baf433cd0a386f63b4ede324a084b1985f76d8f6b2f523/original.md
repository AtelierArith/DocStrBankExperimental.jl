```
RandomThinning(p)
```

Random thinning with retention probability `p`, which can be a constant probability value in `[0,1]` or a function mapping a point to a probability.

## Examples

```julia
RandomThinning(0.5)
RandomThinning(p -> sum(to(p)))
```
