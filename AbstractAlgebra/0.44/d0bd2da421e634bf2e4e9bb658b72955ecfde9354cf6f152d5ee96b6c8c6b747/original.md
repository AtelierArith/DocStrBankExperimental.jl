```
inv!(z, a)
inv!(a)
```

Return `AbstractAlgebra.inv(a)`, possibly modifying the object `z` in the process. Aliasing is permitted. The unary version is a shorthand for `inv!(a, a)`.

!!! note
    `AbstractAlgebra.inv` and `Base.inv` differ only in their behavior on julia types like `Integer` and `Rational{Int}`. The former makes it adhere to the Ring interface.

