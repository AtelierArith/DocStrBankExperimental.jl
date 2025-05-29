Special format that serves as lazy placeholder for `format(T)` in situations where the type `T` is not yet known.

!!! warning
    Never define `format(T)` for a type `T` in terms of `DefaultFormat`. This will lead to indefinite recursion.

