```
(A::KeyedArray)("a", 2.0, :γ) == A[1, 2, 3]
A(:γ) == view(A, :, :, 3)
```

`KeyedArray`s are callable, and this behaves much like indexing, except that it searches for the given keys in `axiskeys(A)`, instead of `axes(A)` for indices.

A single key may be used to indicate a slice, provided that its type only matches the eltype of one `axiskeys(A,d)`. You can also slice explicitly with `A("a", :, :)`, both of these return a `view`.

An extra trailing colon (when all other indices are fixed) will return a zero-dimensional `view`. This allows setting one value by writing `A("a", 2.0, :γ, :) .= 100`.

Also accepts functions like `A(<=(2.0))` and selectors, see `Nearest` and `Index`.
