```
ParabolicSegment(a::Number, h::Number)
```

A parabolic segment with x-intercepts `±a` and a yintercept of `h`.

# Note

This is just a convenience function for `stretched(ParabolicSegment(), a, h)`
