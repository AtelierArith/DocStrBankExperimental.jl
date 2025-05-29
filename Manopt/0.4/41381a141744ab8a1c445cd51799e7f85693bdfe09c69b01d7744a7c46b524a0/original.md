```
|(s1,s2)
s1 | s2
```

Combine two [`StoppingCriterion`](@ref) within an [`StopWhenAny`](@ref). If either `s1` (or `s2`) is already an [`StopWhenAny`](@ref), then `s2` (or `s1`) is appended to the list of [`StoppingCriterion`](@ref) within `s1` (or `s2`)

# Example

```
a = StopAfterIteration(200) | StopWhenChangeLess(1e-6)
b = a | StopWhenGradientNormLess(1e-6)
```

Is the same as

```
a = StopWhenAny(StopAfterIteration(200), StopWhenChangeLess(1e-6))
b = StopWhenAny(StopAfterIteration(200), StopWhenChangeLess(1e-6), StopWhenGradientNormLess(1e-6))
```
