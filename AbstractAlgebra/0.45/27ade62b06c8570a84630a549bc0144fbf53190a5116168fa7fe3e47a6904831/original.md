```
conj!(out::T, g::T, h::T) where {T <: GroupElem}
```

Return `inv(h)*g*h`, possibly modifying `out`. Aliasing of `g` or `h` with `out` is allowed.
