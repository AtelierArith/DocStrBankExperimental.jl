```
sub!(z, a, b)
sub!(a, b)
```

Return `a - b`, possibly modifying the object `z` in the process. Aliasing is permitted. The two argument version is a shorthand for `sub!(a, a, b)`.
