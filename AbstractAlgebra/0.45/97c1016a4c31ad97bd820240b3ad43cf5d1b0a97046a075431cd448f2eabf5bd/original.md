```
div_right!(out::T, g::T, h::T) where {T <: GroupElem}
```

Return `g*inv(h)`, possibly modifying `out`. Aliasing of `g` or `h` with `out` is allowed.
