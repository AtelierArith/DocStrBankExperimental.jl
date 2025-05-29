```
add!(z, a, b)
add!(a, b)
```

Return `a + b`, possibly modifying the object `z` in the process. Aliasing is permitted. The two argument version is a shorthand for `add!(a, a, b)`.
