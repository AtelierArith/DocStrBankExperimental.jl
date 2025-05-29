```
quadgk_print([io], f, args...; kws...)
```

Identical to [`quadgk`](@ref), but **prints** each integrand evaluation to the stream `io` (defaults to `stdout`) in the form:

```
f(x1) = y1
f(x2) = y2
...
```

which is useful for pedagogy and debugging.

Also, like [`quadgk_count`](@ref), it returns a triple `(I, E, count)` of the estimated integral `I`, the estimated error bound `E`, and a `count` of the number of times the integrand `f` was evaluated.
