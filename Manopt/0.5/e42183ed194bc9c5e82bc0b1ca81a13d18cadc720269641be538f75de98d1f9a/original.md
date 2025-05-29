```
&(s1,s2)
s1 & s2
```

Combine two [`StoppingCriterion`](@ref) within an [`StopWhenAll`](@ref). If either `s1` (or `s2`) is already an [`StopWhenAll`](@ref), then `s2` (or `s1`) is appended to the list of [`StoppingCriterion`](@ref) within `s1` (or `s2`).

# Example

```
a = StopAfterIteration(200) & StopWhenChangeLess(M, 1e-6)
b = a & StopWhenGradientNormLess(1e-6)
```

Is the same as

```
a = StopWhenAll(StopAfterIteration(200), StopWhenChangeLess(M, 1e-6))
b = StopWhenAll(StopAfterIteration(200), StopWhenChangeLess(M, 1e-6), StopWhenGradientNormLess(1e-6))
```
