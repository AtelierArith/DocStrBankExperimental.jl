```
mul!(z, a, b)
mul!(a, b)
```

Return `a * b`, possibly modifying the object `z` in the process. Aliasing is permitted. The two argument version is a shorthand for `mul!(a, a, b)`.
