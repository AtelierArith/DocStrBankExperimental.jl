```
powers(t::AbstractTermLike)
```

Returns an iterator over the powers of the monomial of `t`.

### Examples

Calling `powers(3x^4*y)` should return `((x, 4), (y, 1))`.
