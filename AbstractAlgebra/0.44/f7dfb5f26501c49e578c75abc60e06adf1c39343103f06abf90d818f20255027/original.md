```
mod!(z, a, b)
mod!(a, b)
```

Return `mod(a, b)`, possibly modifying the object `z` in the process. Aliasing is permitted. The two argument version is a shorthand for `mod(a, a, b)`.
