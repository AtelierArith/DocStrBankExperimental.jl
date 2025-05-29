```
div!(z, a, b)
div!(a, b)
```

Return `div(a, b)`, possibly modifying the object `z` in the process. Aliasing is permitted. The two argument version is a shorthand for `div(a, a, b)`.

!!! note
    `AbstractAlgebra.div` and `Base.div` differ only in their behavior on julia types like `Integer` and `Rational{Int}`. The former makes it adhere to the Ring interface.

