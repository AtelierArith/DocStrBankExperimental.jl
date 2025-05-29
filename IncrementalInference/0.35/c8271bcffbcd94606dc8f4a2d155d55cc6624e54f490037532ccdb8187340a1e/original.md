```julia
incrSuffix(lbl; ...)
incrSuffix(lbl, val; pattern)

```

Utility for incrementing or decrementing suffix numbers in DFG variable labels, e.g.

```julia
incrSuffix(:x45_4)
# returns :x45_5

incrSuffix(:x45, +3)
# returns :x48

incrSuffix(:x45_4, -1)
# returns :x45_3
```

Notes

  * Change `pattern::Regex=r"\d+"` for alternative behaviour.
